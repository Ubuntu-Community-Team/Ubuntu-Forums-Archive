---
title: "logging in and constant authenication"
date: 2018-05-24
forum: General Help
---

### Post by jgw on 2018-05-24
I am running with ubuntu 18.04 and am coming from 16.04   When I installed it asked if I wanted to have automatic login and it continues to ask me to login with my password.  Everytime I do anything I am also asked to enter my password.  when I goto settings/users it has automatic grayed out and set to on.  If this is the way it is then, I guess, my only option is to login with SU and put a stop to the constant signins.  

Thoughts?

---

### Post by #&amp;thj^% on 2018-05-24
Is this a upgrade then? (If so could be harder to help)
Have a look and see if this also is enabled: **"/etc/gdm3/custom.conf."**
And check if it reads>>**"AutomaticLoginEnable=True"**
And with Nvidia drivers it's best to disable a wayland option via:
Change the line in the same file.
```

#WaylandEnable=false
```

to
```

WaylandEnable=false
```
A reboot is probally best.
To reverse seems pretty straight forward.

---

### Post by jgw on 2018-05-24
This was a clean install (got rid of all existing partitions, etc).  
automatic login is true and my password is on the line after that.  Everything else in  that file is hashmarked.

I am running with radeon 7 graphics (the radeon driver I think (not sure but that is what 16.04 used and it works - actually better than the one I had several weeks ago!  (I am running it on my 4K tv with a LOT less problems than I had under 16.04!  Leads me to believe work has been done!)

It also asks me to login if I leave the machine for about 5 minutes.  There was once a setting for that but the change in the settings have tended to obscure a lot of what I have become used to.
But, everytime I run anything I have to login, even if I have left it open in the launcher.  SU is also a pain to run under as it starts in a different place and I am having problems knowing what I am dealing with.  I have everything hooked into a kvm in which the mouse doesn't transfer anymore so I have multiple mice to deal with too (have another box, just too lazy to hook it up I guess <sigh) Anyway, for instance, this is my main machine, still on 16.04 and then I have the machine on 18.04 also running and, sometimes, I forget which machine I am dealing with (I have one other also connected) and myu mind is not as good as it once was due to years of use <G>)  

I had been having a lot of problems with the machine that is running 18.04 so I thought I would reset it with a new operating system.  I had, for instance, the network magically stopping working whilst thinking it was still on.  (I now have another machine doing the same thing so I will have to move that one up too)

Anyway, thanks for the reply!

---

### Post by VMC on 2018-05-24
I don't have ubuntu, but on xubuntu, I have "/etc/lightdm/lightdn.conf":
 [Seat:*]
...
autologin-user=<your user>
autologin-user-timeout=0
...

I also don't use Wayland

---

### Post by #&amp;thj^% on 2018-05-25
Also look at VMC's post.
Well I have only a couple of things to check then:
Lets be sure permissions are set properly for example:
.Xauthority
```
ls -lah
-rw-------  1 me   me     56 May 25 05:53  .Xauthority
-rw-------  1 me   me   4.3K May 25 05:53  .ICEauthority

```
And /tmp
```
ls -ld /tmp
drwxrwxrwt 16 root root 4096 May 25 06:40 /tmp

```
Look also at Status of your usser account
```
sudo chage -l me
Last password change					: May 02, 2018
Password expires					: never
Password inactive					: never
Account expires						: never
Minimum number of days between password change		: 0
Maximum number of days between password change		: 99999
Number of days of warning before password expires	: 7

```
Hint: change "me" to your user name.
And perhaps logs hopefuly may give a clue.
```
sudo less /var/log/auth.log >aut.log.txt

```
This will leave a text file in your home directory to veiw or share.

---

### Post by jgw on 2018-05-25
Thanks for the reply!

Here are some results from running the aforemention
-rw-r--r--  1 root root  184 May 21 16:24  .wget-hsts
drwx------  2 root root 4.0K May 21 13:42  .gvfs
drwxr-xr-x  4 root root 4.0K May 23 16:33  ..

greg@movies:~$ sudo chage -l me
[sudo] password for greg: 
chage: user 'me' does not exist in /etc/passwd
greg@movies:~$ sudo less /var/log/auth.log >aut.log.txt
greg@movies:~$ 

I have seen 'me' in several files which may be a real problem if its supposed to be the password file?

---

### Post by #&amp;thj^% on 2018-05-25
> **jgw said:**
> Thanks for the reply!

Here are some results from running the aforemention
-rw-r--r--  1 root root  184 May 21 16:24  .wget-hsts
drwx------  2 root root 4.0K May 21 13:42  .gvfs
drwxr-xr-x  4 root root 4.0K May 23 16:33  ..

greg@movies:~$ sudo chage -l me
[sudo] password for greg: 
chage: user 'me' does not exist in /etc/passwd
greg@movies:~$ sudo less /var/log/auth.log >aut.log.txt
greg@movies:~$ 

I have seen 'me' in several files which may be a real problem if its supposed to be the password file?
Sorry you forgot I mention to change **"sudo chage -l <youruser name>"** "me" is my user name. :)
Hint: change "me" to your user name.

---

### Post by jgw on 2018-05-25
Thanks for the help.  My problem with the username thing is that I have noticed several files with 'me' as the owner.  I remember when I saw that I thought that was a system show for my name (greg).  So, if I run into any of those I should change the owner to 'greg' or just put 'me' into the password file?

Is there a place to set the password after sleeping thing?

---

### Post by #&amp;thj^% on 2018-05-25
No don't put "me"  into any password file...I hope I have not confused you with my meaning myself, "me" is my **user name**
```
$ whoami
me

```
So it should be just you "greg" in any of those case's. :)
Sorry if I was not detailed enough. :(

---

### Post by kerry_s on 2018-05-25
open passwords & keys, right click on login-> change password, enter your current password, leave the rest blank

---

### Post by yancek on 2018-05-25
> It also asks me to login if I leave the machine for about 5 minutes.   There was once a setting for that but the change in the settings have  tended to obscure a lot of what I have become used to.

The screen lock function can be found by clicking the Activities tab in the upper left of the Desktop, in the search bar type settings, click the settings icon, in the left panel of the new window click on Privacy and on the right of the window you will have a number of options, the top one being Screen Lock.  Click on Screen Lock and the new window will allow you to change settings including turning it off.

The autologin is also in Settings, click on Details at the bottom of the left panel and in the new window on the upper left, click on Users and the autologin option is on the right.  It will be greyed out so click the unlock tab in the upper right of the window and enter your pimary user password to make a change.

---

### Post by jgw on 2018-05-26
Thanks for the replies!

"passwords & keys"?   Where is that?  (googled "ubuntu 18.04 "passwords & keys" and got over 12,000 responses which confused), did a settings search to no avail)

Thank you...........

---

### Post by kerry_s on 2018-05-26
> **jgw said:**
> Thanks for the replies!

"passwords & keys"?   Where is that?  (googled "ubuntu 18.04 "passwords & keys" and got over 12,000 responses which confused), did a settings search to no avail)

Thank you...........

just click on the applications & type "passwords", it only to "pa" on mine to bring it to the top.

sorry have to cover, it has my email.

[ATTACH=CONFIG]279872[/ATTACH][ATTACH=CONFIG]279873[/ATTACH]

---

