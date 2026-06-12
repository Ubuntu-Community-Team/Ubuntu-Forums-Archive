---
title: "Ubuntu 14.04 - Unity &quot;Untitled window&quot; extra icon confusion"
date: 2014-08-18
forum: General Help
---

### Post by alex241 on 2014-08-18
New to Ubuntu.
In order to experiment with Unity icon creation and activation, I did:
1. Compile an X "Hello World" C program resulting in an executable "hello-x".
2. Write a basic "Desktop" file,
 /home/alex/.local/share/applications/hello-x.desktop

Version=1.0
Type=Application
Name=Hello World Alex!
Icon=/home/alex/my_dog.png
Path=/home/alex/
Exec=/home/alex/hello-x
Terminal=false
StartupNotify=false
#OnlyShowIn=Unity;
X-UnityGenerated=true
Categories=Utility;

3. Run the "hello-x" application (from a terminal):

/home/alex/hello-x

3.1.  I get a nice little "Ubuntu"-type window showing "Hello, World!".
As expected.  Perfect.

3.2.  I get a grayish icon named "? Untitled window" on the "Launcher".
OK, I suppose.  Nothing to write home about (yet).

4.  Right click on the icon, select Quit.  The program exits.
Here, as expected.  Fine.


5.  Go to the "Dash".  Under "Applications" I find the icon associated with
my application (/home/alex/my_dog.png).
Drag icon to the Launcher, it locks solid.
As expected.  Perfect.

6.  Left click on icon to start my application.  The application starts
(i.e., the window showing "Hello, World!" is displayed).
As expected.  Perfect.

7. PROBLEM
At the same time as application starts (step 6. above) a SECOND icon,
"? Untitled window" (same one as at 3.2. above) shows up in the Launcher.

Second icon UNEXPECTED.  NOT NEEDED.  Total confusion.

I expected:
7.1.  Click on first icon (the good one) ->  The application starts.
7.2.  Exit the application by either clicking the "X" button of its window
      or on the INEXISTENT "Quit" choice of the main application icon.

NOTES:

N1.  Making the Desktop file executable doesn't make any difference.

N2.  Running my application from /usr/bin doesn't make any difference:
 ln -fs /home/alex/hello-x /usr/bin/hello-x
 Change the "Exec=" in the Desktop file accordingly.

N3.  While running, right click on "? Untitled window" icon, Quit.
     The application quits (exits) as expected.


Please help.
Thanks,
-- Alex

---

