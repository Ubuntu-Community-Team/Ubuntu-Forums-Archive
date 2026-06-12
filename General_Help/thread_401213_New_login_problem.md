---
title: "New login problem"
date: 2007-04-04
forum: General Help
---

### Post by Tanis on 2007-04-04
Been using ubuntu 6.10 for some months now and it has been working fine.
This morning I restarted after the latest two updates were installed.  I think they had something to do with db files I don't remember.
After restarting and loging in, well it just dosent login.  It begins to bring up natalius and then goes back to the login screen.  If I try to login again it tells me that I already have a sesion running.  But I can't get past this point, not even if I login in safe mode.
Tried rebooting and trying again.  Same thing.
I have a second account for problems.  And I tried to login to it and I get the same thing.

Anyone have some Idea what went wrong.
Havent been changing or installing anything resently.  Just the normal updates that come down the pipeline.


Thanks
Ron

---

### Post by acormack on 2007-04-04
can you log in via ctrl + alt + F1 in text mode

if so try

sudo apt-get update
sudo apt-get upgrade

then reboot and try again,

---

### Post by Tanis on 2007-04-04
as to ctrl+alt+F1 that I can do.
but the update / upgrade didn't do any good.

Still stuck in the loop of login.
There are no errors on login.  It just cycles around and back to the login.  Never loging in.

---

### Post by AlzBrain on 2007-04-04
I am having the same problems here. The system was ok for several months. Then yesterday, after the update, I've shutdown the computer. Today, when I booted it up, the login screen appears, I log in and it seems the graphic mode is shutdown, and then it starts again and returns to the login screen.

I really wouldn't like to install it again.

---

### Post by AlzBrain on 2007-04-04
Guess I've solved it. 

It seems the last update did something to my video driver config. Had to reinstate it.

If your video driver card is nVidia, I suggest downloading and installing the latest driver and starting over.


Good luck!

---

### Post by nuklehed on 2007-04-04
I am having the same trouble. Is there a way to fix it without have to reinstall the latest nvidia drivers? What file did the latest update modify?

---

### Post by AlzBrain on 2007-04-04
My video card is a nVidia. 

If your card is also a nVidia, you can download the drivers from [http://www.nvidia.com](http://www.nvidia.com)

Otherwise, search for a how-to install your video card drivers before proceeding.

Regards,
AlzB

---

### Post by beefcurry on 2007-04-05
Yup, I had this exact problem and re-installing my Nvidia drivers solved it.

---

