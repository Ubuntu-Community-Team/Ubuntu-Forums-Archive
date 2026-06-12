---
title: "Customize Ubuntu LiveCD with script running at boot"
date: 2017-12-19
forum: General Help
---

### Post by napox on 2017-12-19
Hi,

I'm trying to customize Ubuntu LiveCD (14.04) with a script running at boot.

I extract **filesystem.squashfs** file, I added my script to run at boot.
I added the file name to run at **/etc/rc.local** (of the extracted **filesystem.squashfs**)
And close the **filesystem.squashfs** file.

I moved the **filesystem.squashfs** file to the LiveCD and when the LiveCD boot script runs well on boot and does exactly what I wanted.
But it doesn't output anything to screen.

How I force it to output to screen ?
Thanks.

---

### Post by ian-weisser on 2017-12-19
It's not a matter of "forcing" output anywhere.
Your script is probably running before an output display gets assigned.
The display gets assigned after a user logs in.

If your script runs before that, it should output to log instead of display.

---

### Post by napox on 2017-12-19
Thanks for the answer, Ian.

What are my alternatives for sending output to the screen on boot ?

---

### Post by ajgreeny on 2017-12-19
It might help to know what you are wanting to see; perhaps a sleep time before the script runs or similar to allow the display to become active will do what you want, but as we don't know what that is, we are not going to be very much help to you.

---

### Post by napox on 2017-12-19
Hi ajgreeny,
I just want to see the output of the script in a simple shell window (some **echo **prints or in any other way).
In the **rc.local** file there is **sleep 10** before the script starts.

---

### Post by ian-weisser on 2017-12-19
> **napox said:**
> I just want to see the output of the script in a simple shell window (some **echo **prints or in any other way).

Then your script needs to figure out which $DISPLAY is active,
Or your user autostart needs to run the script instead.

Your requirement to use an obsolete tool like rc.local limits your flexibility on this.
You are also going to run into permission problems when root tries to open a display window on a user desktop. Wayland (17.10 and newer) won't let you do that.
Remember that unnecessary and out-of-sequence tasks slow your boot.

Example: I would have a user-level process triggered by ~/autostart (which runs after $DISPLAY is active) read run the script. A separate script for the root elements can be easily triggered by a dbus message from the user-level script.

---

### Post by napox on 2017-12-28
Hi Ian,
I wanted to take your advice and add my script to  [COLOR=#000000]~/autostart[/COLOR] but when I look inside the  **filesystem.squashf** file I see /home is empty and there isn't any accounts there. When I boot the Ubuntu from the disk on key with same  **filesystem.squashf **file there is Ubuntu account under /home/ubuntu
Can you explain me how I add my script in this case ?
Thanks ahead.

---

