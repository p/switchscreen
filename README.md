
Introduction
------------

switchscreen is a program that switches the pointer of an X server
between different screens that the server manages.  It allows making a
dualhead setup behave as two totally independent desktops, and
toggling the screen by hitting some key.

Compiling should only be a matter of typing "make" (provided the
necessary development packages are installed).

For usage information, type "switchscreen -h".

Included is also a script, togglescreen.sh, which toggles between
screens 0 and 1, and stores the position of the pointer on the other
screen.


Dualhead functioning
--------------------

switchscreen can be used to switch between two independent screens of
an X server, thus allowing two totally independent desktops using the
same keyboard and mouse.  You can then toggle between the screens
using any hotkey you wish.  To configure XFree86 for such operation do
the following:


1.  Configure your X for dualhead support (_without_ Xinerama!).

2.  Define in the ServerLayout section the second screen's position to
    be farther away than the first screen's width.  For example, if
    your first screen has a resolution of 1600x1200, you might define

      Screen "Default Screen"   # 1600x1200
      Screen "Secondary Screen" Relative "Default Screen" 1700 0

    This stops the mouse from moving from the edge of the first screen
    to the second screen.

3.  Configure your startup scripts to start a window manager on both
    screens (normally screens :0.0 and :0.1).

    Note that some window managers and/or desktops may have problems
    running two sessions for the same user at the same time.  For
    instance, I use GNOME and sawfish on the primary display, and
    fvwm2 on the second.

4.  Configure both window managers to run the script togglescreen.sh
    when you hit some hotkey, eg. alt-tab.


Bugs
----

With version 0.1.0, in some cases switching to the second screen the
focus doesn't immediately change to the window containing the pointer
before it has been moved to another window and back.

In version 0.1.1 a patch from Javeed Shaikh has been applied that
reportedly fixes this problem.  I have not tested the new version, and
I recommend testing for yourself which version works better for you.

In (the unofficial) version 0.1.2 the ID of the last focused window gets saved.
This fixes a focus issue with dwm.


Legal jabber
------------

switchscreen is distributed under the GNU General Public License
version 2 or, at your option, any later version.  Basically you may
use, modify and distribute the program in any way you wish, provided
that the source code to any modifications distributed is made
available under the GPL too.  You may find the exact terms of the GPL
in the file COPYING, distributed in the package.

I take absolutely no responsibility for any harm this program might
do.  If it breaks, you get to keep both pieces.


switchscreen is copyright (C) 2003 by Sampo Niskanen <sampo.niskanen@iki.fi>
Feedback on the program is always welcome.

