---
title: "update manager admin prompt failure"
date: 2007-11-19
forum: General Help
---

### Post by raydar on 2007-11-19
I'm running UbuntuStudio 7.10.

When the update-notifier tells me updates are available, I click the notifier icon in the panel, and the update manager starts, but the admin password prompt never appears (screen doesn't dim or anything).  The update manager just sits there waiting, with a "busy" mouse pointer if I hover over it.  

To get the update to happen, I have to end the update manager process (it won't close normally), click on the update-notifier icon in the panel again, and on this second try, the update manager starts and the admin prompt *does* appear.

Anybody know why the admin prompt process would fail to start on the 1st try?  I've usually had a few things running when this happens, like browser, e-mail, & vmware, but as far as I can tell I'm not doing so much stuff that I'm not giving the prompt process a chance to start--not sure that's possible anyhow.  And it works the 2nd time, always.

Thanks for any help!

---

### Post by kshane on 2007-11-19
> **raydar said:**
> I'm running UbuntuStudio 7.10.

When the update-notifier tells me updates are available, I click the notifier icon in the panel, and the update manager starts, but the admin password prompt never appears (screen doesn't dim or anything).  The update manager just sits there waiting, with a "busy" mouse pointer if I hover over it.  

To get the update to happen, I have to end the update manager process (it won't close normally), click on the update-notifier icon in the panel again, and on this second try, the update manager starts and the admin prompt *does* appear.

Anybody know why the admin prompt process would fail to start on the 1st try?  I've usually had a few things running when this happens, like browser, e-mail, & vmware, but as far as I can tell I'm not doing so much stuff that I'm not giving the prompt process a chance to start--not sure that's possible anyhow.  And it works the 2nd time, always.

Thanks for any help!

Is it possible the PW prompt is behind the program?  I've had few things in Gutsy do this - the prompt for password showing up behind the application...

Kevin

---

### Post by raydar on 2007-11-20
I suppose it's possible, although sure can't find it as a process to switch to with Alt+Tab or on the panel with other running processes.  I wish I could recall whether I've found it in the System Monitor's process list, but I can't.

I got another update this morning, and the problem didn't recur this time, but I had only Thunderbird running when I clicked the notifier icon to start the update manager.  Maybe some other process was indeed interfering and I just have to get lucky to have the "right" stuff running in order to repeat the problem for troubleshooting.  (I suspect vmware if anything, since it has a nifty mouse-capture feature and routes keyboard input to the virtual machine whenever the mouse pointer happens to be over the vmware window, etc.)

---

### Post by glucosegrin on 2008-01-17
I'm running 7.10 as well, and I'm having the same "problem", but I have worked around it.

I'm running on a Toshiba Satellite 1110CS, which is a 1.8 Celeron with 256MB of ram, so when I hit the "Install Updates" button, it takes some time before the password prompt shows itself.  If I or somehow take focus away from Update Manager before or while it says "Starting Administrative Application" (or whatever) in the taskbar, the password prompt never appears and Update manager stays grey'd out.  I've moved windows around, switched desktops, and otherwise poked around to find the password prompt, it just won't show itself.  

I don't mean to drag up an old thread, but this is all I found when searching for an answer.

---

### Post by raydar on 2008-01-17
I just happened to have it occur again yesterday or the day before, though there haven't been many updates for a while.  I think you must be right; I've gotta keep that in mind next time and just sit on my hands to keep me from going off on a tangent while waiting for the Update Manager & admin prompt to load, however long that may be. 

May not be the freshest thread, but this still seems like something that shouldn't happen, or at least shouldn't stick a user with having to kill the update manager and restart it.  I'm non-noob enough to know how to do that and be inclined to do that, but some other, more obvious way to recover would be great.

(Perhaps the Hardy Heron gods are listening?  Or, I oughta learn how fix it myself with a little coding & recompiling--this is Linux, after all! :) )

---

### Post by daveofdave on 2008-05-04
Hi guys I have the same problem after upgrading to hardy heroin from gutsy which used to be ok , I left update manager running for 4 hours waiting for the login window to appear but no luck !
The only way for me to stop the  update manager now is to use the force quit application.
don't know what to do now ?
Help

---

### Post by variableenigma on 2008-05-07
I am having this problem since I upgraded to Hardy Heron. 

Everytime I try to install my many, many updates, I get a "Starting Administrative Application" box in the taskbar, but then nothing happens, it eventually goes away, and the Update Manager dims and crashes.

I have also recently tried to install Wine (to attempt to play WoW), but when I input the "sudo" command, I get this output:
"amanda@amanda-laptop:~$ sudo
sudo: unable to resolve host amanda-laptop"

I assume that these issues are stemming from the same underlying problem, since they are both asking the computer to promt me for my password.

Any suggestions?

---

### Post by linuxguiri on 2008-05-16
same problem here on a dell inspiron 9400 running hardy heron.

don't know if this is related but i think there's some changes in how ubuntu handles file permissions since it tells me i can only permanently delete files rather than move them to the trash.

possible solution: [http://ubuntuforums.org/showpost.php?p=4961730&postcount=12](http://ubuntuforums.org/showpost.php?p=4961730&postcount=12)

---

### Post by ranthony on 2008-05-20
I'm having the same problem on one of the systems I've upgraded to Hardy, the other continues to function normally.  I can get apt-get to work in terminal with no problems; the gui interface for update-manager locks up trying to start "administrative application" (although I can sometimes get the password dialog to come up after ending the update-manager process in system monitor) seems like it might be related to display issues...?

Since apt-get continues to work, the failure of the gui isn't a pressing issue; still, I'd like to know what the cause is.

-RAnthony

---

### Post by Xirowei on 2008-05-28
I new user to Ubuntu 8.04 Desktop. The problem of Starting Administrative Applications, Prompt Password problem occur to me after i update the Ubuntu. After update, if i type sudo, i will get below error message.
sudo: unable to resolve host xirowei
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...

Before update Ubuntu, if i type sudo gedit /boot/grub/menu.list, it will show the content of the menu.list. But since after update it will just show a blank file. However if type cat /boot/grub/menu.list, all the content can be shown.

Currently i found a quick method to solve the Starting Administrative Application not shown problem. Please run System Monitor, go to Processes, find "**update-notifier**" and **End Process**. Now the Starting Administrative Application will show. Why it will show after do this i also no idea as I'm newbie to Linux >.<"

---

### Post by snowolfedu on 2008-05-28
I also was having this problem (Hardy 8.04) with Update Manager and some of the other Admin related activities - no password screen would appear and Update Manager would become unresponsive.

Based on a link earlier in this thread it appears that the problem is probably network related - Gnome runs on X which is a network protocol for GUI handling (in case you didn't know).

I had just recently (just prior to the problem appearing) changed my domain name - so I reset it using ...

#hostname *myhost*

I also used vi to remove references to the 'bad' host/domain in /etc/hosts and /etc/resolv.conf - I did also reboot my machine just to make sure everything was reset although restarting the network should be enough.

Everything works again. Hope this provides a suitable fix for others

---

### Post by 47_MasoN_47 on 2008-05-30
I had the hostname problem also.  I went to System>Administration>Network and made sure the host name in the General tab was also the same as 127.0.0.1 and 127.0.1.1 in the Hosts tab.  It started working immediately after that.

---

### Post by WackyCat on 2008-06-08
47_MasoN_47  THANKS!! I was having multiple problems with updates and Synaptic...your hint solved them immediately.

---

