---
title: "can't get past logon splash screen"
date: 2015-04-11
forum: General Help
---

### Post by sumithar on 2015-04-11
Hi,
After a long gap I decided to give my Ubuntu install another whirl.  Problem was I had forgotten my password.  I did the business with booting into recovery and reset my password.  Then I did the regular boot into my logon screen and entered the new password.  The logon screen disappeared, a console flashed with some commands, too fast to read anything and presto the logon screen reappeared.  I tried a couple times and then went into one of the terminals Ctrl Alt F1 and was able to successfully logon from there.
I checked online and one thread to logon from a terminal session and type 
sudo chown -R $USER:$USER $HOME
then go back to Ctrl Alt F7 and try to logon again.
I tried this but it didn't work.

Any thoughts, suggestions?

---

### Post by dino99 on 2015-04-12
which ubuntu is it ?
the easiest way is to create a new user account, as your actual profile seems borked

---

### Post by sumithar on 2015-04-12
Hi,
I am on 14.04.
I did as you suggested and created a new user from the command line.  I rebooted and tried to log in from the log in screen using this new id but got the same result.  This time I managed to read a bit of the terminal messages especially the file name /etc/default/saned and googled it which led me to this page
[http://askubuntu.com/questions/393180/ubuntu-12-04-cannot-start-saned-disabled-edit-etc-default-saned](http://askubuntu.com/questions/393180/ubuntu-12-04-cannot-start-saned-disabled-edit-etc-default-saned)

Per instructions on this page I removed my nvidia drivers and reinstalled them.  FWIW before I could do this, I got some apt error messages that I had to sort out.  But long story short, I reinstalled the nVidia drivers and rebooted.

Now when I type the password on the log in screen it gives me a pretty much blank screen (with the purplish shades of the login splash screen colors).  It pops up a box saying System errors occurred Report/Cancel.  I tried both options and it did nothing, the box went away and I had a blank screen.  Do I have to reinstall Ubuntu?

Thanks!

---

