---
title: "Login help - main user account won't log on, even after password reset"
date: 2013-11-06
forum: General Help
---

### Post by whitelouis on 2013-11-06
Hey guys! 

I've searched and found threads close to my problem, but none seem to go  quite far enough to solve the problem...stay with me, this may get a  little long winded, but I'd like to be thorough to hopefully help you  help me more easily. :smile:

I'm running Ubuntu 12.04 LTS server edition, with the default  Ubuntu/gnome GUI. It's primary use is as a personal development server  for PHP, MySQL, Javascript, Java, and JQuery. It's also got tons of disk  space, so it's my home file server for multimedia as well.

Yesterday I was attempting to update Samba from 3.6.3 to 4.1 (stable)  via tarball downloaded from Samba's site. I removed and purged smbd,  then went through with creating a directory - /usr/local/src - to  extract the Samba 4.1 tarball into, proceeded to chown that directory,  ./configure 'd, then used 'make' to install. All seemed to go well, and  finally I used checkinstall. This led through a few options, the last of  which I don't remember the words of exactly, but my interpretation was  that there were excess files from the intsall which were nolonger  necessary, and would I like to view them? Default was no, but wondering  what they were, I hit y and perused through them pretty quickly, when I  got to the end it simply said (END), but wouldn't let me do anything  else with the terminal window.

I tried a variety of things, but none seemed to do anything, so  eventually (against my better judgement) I just closed the terminal,  despite the warning that there was still a process running in it.

I did a quick ls /etc/init.d to see if the new version of Samba was  running, but found it not listed, so I rebooted, momentarily falling  back to my years of Windows experience.

When I tried to log back in, I was greeted with repeated "Invalid  password" notices upon entering the same password I've had on the  machine since I installed, and have never had an issue with. Guest  account worked (obviously) but that's not much help.

Thinking perhaps the password had been altered through something I did, I  rebooted into recovery mode, dropped to the shell as root, used 'mount  -o rw,remount /' and then 'passwd [user]', entered a new password twice,  was told it was successful, exited, resumed normal bootup, got to the  log on screen and had the same issue.

Thinking maybe the GUI was to blame, I used CTRL+ALT+F1 to get out of it  and tried to log in that way, but every time I enter the username and  password, it just flashes back to the same "username" prompt. No errors,  nothing, just as if I hadn't ever typed anything. I even changed the  password to "a" just to test it, and entered it 30 or so times out of  stubborn frustration, to no avail.

The only other thread I found with a near identical issue resulted from  an over-liberal use of chown on the /usr directory, but after checking  ownership/permissions with 'ls -l /usr' and 'ls -l /usr/local' via the  recovery root shell, it seems all directories in both are root:root  except the /usr/local/src directory I created, which is [user]:root.

Sorry that was a lot of info, but that's the last thing I had done  before the issue arose. I'm pretty sure those are all the commands I  used, after installing - via 'apt-get install' - a bunch of  dependencies. 

If it comes to it, having to re-install isn't the end of the world, as I  don't have any really important files on the physical drive Ubuntu is  on, and can use the live-disc first to move any files that I want to  keep, but it'd be great to use this as a learning experience and figure  out how to fix it!

Thanks in advance for your help!

---

### Post by steeldriver on 2013-11-06
Hello and welcome to the forums

The (END) probably just indicated that the installer was using the 'less' program to paginate the output - pressing 'q' (for quit) would likely have got you out of it cleanly

It's hard to imagine what could cause a virtual terminal (Ctrl-Alt-F1) login to fail with NO message - at a minimum you should get 'Login incorrect'. The only thing I can suggest is you reboot into recovery mode again, but instead of choosing root shell, choose the option to fix broken packages. In fact if it was me I'd probably connect via wired ethernet, then choose 'enable networking', THEN 'fix broken packages'.

---

### Post by whitelouis on 2013-11-07
Thanks!

I tried doing all of the above - hardwired connection, enable networking, fix broken packages - and it checked and updated a few things, but none of them were samba, and it ultimately freed about 2MB. Also, it didn't seem to fix my problem :/

In the virtual terminal if I try to log in with the wrong password, it tells me login incorrect, but if I enter the correct password, it erases everything (the password prompt, the login inccorect message, etc) and just shows the OS info at the top, and "Server login:", as if nothing had been entered and it's still waiting for me to log in.

Thanks for the idea!

---

### Post by steeldriver on 2013-11-07
Maybe something in your .profile or .bashrc that's causing you to be logged out as soon as you log in?

---

### Post by whitelouis on 2013-11-07
A) I'm assuming I need to use the root recovery shell to access those, but don't know the exact steps? and B) What should I be looking for when I do open/edit them?

Thanks.

---

### Post by steeldriver on 2013-11-07
well you could start with

```

diff /etc/skel/.profile /home/*username*/.profile

diff /etc/skel/.bashrc /home/*username*/.bashrc

```

If you need to edit from the recovery shell you will likely need to remount the filesystem with read-write permissions

```

mount -o remount,rw /

```

You could always back up your .profile and/or .bashrc and just copy fresh ones from /etc/skel

---

### Post by whitelouis on 2013-11-09
Thanks for the tips. I tried using the diff command for both of those,  and got nothing, it just came up with a new prompt line, waiting for  another command. When I purposefully typed the names wrong - .profilex -  it told me the file didn't exist. I also tried copying both  /etc/skel/.profile and .bashrc into my /home/user/ directory, but again  to no avail. 

It seems like whatever I did to screw this up,  isn't something very easily fixable...chances are I'll just give up on  it and re-install tomorrow...

Thanks for your help though.

---

