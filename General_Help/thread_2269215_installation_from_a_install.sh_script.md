---
title: "installation from a install.sh script"
date: 2015-03-14
forum: General Help
---

### Post by wstay3 on 2015-03-14
Can someone please explain why my installation from a install.sh script returns an error message: 'install.sh: command not found'. Please refer to the attachment with this post.

---

### Post by kerry_s on 2015-03-14
chmod +x install.sh
sudo sh ./install.sh

---

### Post by CaptainMark on 2015-03-14
Yeah, by using install.sh you are telling the terminal to look for already installed programs called install.sh, which it's unlikely you have. use this instead to run scripts
```
./install.sh
```

---

### Post by flaymond on 2015-03-14
chmod +x to make it executable and run it with this ./

In more clear way

```


cd /the/directory        # go to directory where the file exist.

chmod +x install.sh     # make install.sh as executable          

./install.sh         # run the script. You can run it as sudo if it **does** really need root permission (sudo ./install.sh)


```

If you don't want to type .sh extension everytime you wanna run it...just do **mv install.sh install** (This will change the name of install.sh to install without making any change in the contents.

---

### Post by nerdtron on 2015-03-14
Or if you know that the program uses the bash shell. (since it has a file extension of .sh)

Simply run it on bash:

```
 bash install.sh 
```

---

### Post by wstay3 on 2015-03-15
I can start the installation using the bash sh.
There are problems encountered during installation.
Please refer to attachment with this post.
Any help to these others problems would be appreciated.

---

### Post by flaymond on 2015-03-15
Can you tell us what the install script for? It seems required Qt libraries.

---

### Post by Impavidus on 2015-03-15
It says```
sudo: unable to stat /etc/sudoers: No such file or directory
```That's a pretty serious error. The first time the script complains about Root priviliges [sic], so I think **sudo bash install.sh** is the way to go, but it seems your sudo is messed up. Have you done anything to tweak your sudo?

---

### Post by Yellow Pasque on 2015-03-15
> **Impavidus said:**
> ]That's a pretty serious error.

No, it's complaining that it can't read /etc/sudoers file, which is correct (non-root users/processes can't see the file for security reasons).

---

### Post by wstay3 on 2015-03-16
The install.sh script is for my Samsung All-In-One Printer and the script is from the CD provided with the Printer.
I don't know what went wrong or what I did wrong.
I was shutting down my computer after trying the bash install.sh and having problems as in the screenshot I posted.
My computer hung (it won't shut down) for quite a while. So I just press the Shut-Down button on my computer to turn it off.
When I turn on my computer again, I cannot log-in to my computer.
I got an error message: 'The system is running in low-graphics mode.
Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself'.
Is there a way to correct these settings and configuration.

---

### Post by Impavidus on 2015-03-16
> **Temüjin said:**
> No, it's complaining that it can't read /etc/sudoers file, which is correct (non-root users/processes can't see the file for security reasons).
Running **sudo bash install.sh** (which I think is the correct command to use) gave an error. This error didn't come from the script, but from sudo. That shouldn't happen.

I know non-root users can't **read** /etc/sudoers, but they can **stat** it. Furthermore, /usr/bin/sudo is setUID root (it would be quite useless otherwise), so it **can** read /etc/sudoers.```
$ stat /etc/sudoers /usr/bin/sudo
  Bestand: ‘**[COLOR=#ff0000]/etc/sudoers[/COLOR]**’
  Grootte: 745          Blokken: 8            IO-blok: 4096   normaal bestand
Apparaat: 807h/2055d   Inode: 131283       Koppelingen: 1
Toegang: (**[COLOR=#ff0000]0440/-r--r-----[/COLOR]**)   UID: (    0/    root)   GID: (    0/    root)
Toegang:   2015-03-15 18:00:13.936188652 +0000
Gewijzigd: 2014-02-10 19:16:26.000000000 +0000
Veranderd: 2014-04-19 16:11:26.239499863 +0000
Ontstaan:  -
  Bestand: ‘**[COLOR=#ff0000]/usr/bin/sudo[/COLOR]**’
  Grootte: 155008       Blokken: 304          IO-blok: 4096   normaal bestand
Apparaat: 807h/2055d   Inode: 1578385      Koppelingen: 1
Toegang: (**[COLOR=#ff0000]4755/-rwsr-xr-x[/COLOR]**)   UID: (    0/    root)   GID: (    0/    root)
Toegang:   2015-03-15 18:00:13.872188655 +0000
Gewijzigd: 2014-02-10 19:16:30.000000000 +0000
Veranderd: 2014-04-19 16:11:34.475500204 +0000
Ontstaan:  -

```Not being able to shutdown may also indicate a problem getting root permissions. The low graphics mode indicates a graphics driver problem. It may be possible to fix these things from recovery mode, but with such a diverse collection of problems without a clear cause I'm already leaning towards reinstall.

Maybe you can boot into recovery mode from grub and select "resume" to get a graphical login using the open source drivers. Then run```
ls -ld /etc /etc/sudoers /usr/bin/sudo
```at least to rule out the more serious problems I suspect. If that doesn't work, try it from recovery mode -> root shell. On a good system it should give the response```
drwxr-xr-x 145 root root  12288 mrt 16 10:28 /etc
-r--r-----   1 root root    745 feb 10  2014 /etc/sudoers
-rwsr-xr-x   1 root root 155008 feb 10  2014 /usr/bin/sudo
```(exact numbers may be different)

---

### Post by wstay3 on 2015-03-20
Dear 
 	[**[COLOR=#000000]Impavidus[/COLOR]**]("http://ubuntuforums.org/member.php?u=1417721") 	 
 						
I boot into recovery mode from grub and select "resume" and on to 'Exit to console login'.
I got a blank screen and after a while I have to press ctrl+alt+enter to get a console login from a terminal.
I enter code: 'stat /etc/sudoers /usr/bin/sudo' and got something in the console like what you had posted.
I also enter code: 'ls -ld /etc /etc/sudoers /usr/bin/sudo', I get

'-r--r----- / root root 745 Feb 11 2014 /etc/sudoers
-rwsr-xr-x / root root 156708 Feb 11 2014 /usr/bin/sudo'

From this, would it be possible to find where my problem is?

---

### Post by Impavidus on 2015-03-20
That output seems OK, so I've no idea why **sudo bash install.sh** triggered an error message from sudo. I think that was the right command to use, but sudo didn't even ask for your password and threw an error message right away, indicating it is broken. I'm wondering, maybe the hard reboot cut an automatic update short. When you boot into recovery mode, there is an option to fix broken packages. Try that, it may not help, but won't harm either. Can you login to your desktop? If so, try the **sudo bash install.sh** again.

---

### Post by wstay3 on 2015-03-22
Dear Impavidus,

Thank you for your reply.
I boot into recovery mode and tried the option to fix broken packages.
The console/terminal just run a few lines and stop there.

I am not able to login to the desktop.
Getting to the console from the recovery mode, my monitor screen is just blank (dark/black screen).
I have to press ctrl+alt+F1 (sorry, earlier post, wrong typing: ctrl+alt+enter) to get to a terminal login.
From the console/terminal, I post: startx. It gives me some error message.
And ctrl+alt+F6 or ctrl+alt+F7 to get to the Desktop login from the terminal, just give me a blank screen.
If there is no other way to login to my desktop, guess I just have to do a new/reinstall.

---

### Post by wstay3 on 2015-03-29
> **Impavidus said:**
> ................. sudo didn't even ask for your password and threw an error message right away, indicating it is broken. I'm wondering, maybe the hard reboot cut an automatic update short.

I experiencedd quite often that when shutting down the computer after having closed all of the running programs that I had opened and that I knew of, the computer seem to hang (it won't shut-down). After waiting for 15 minutes to 20 minutes to half an hour it still won't shut-down, I simply pressed the Shut-down button on the conputer casing. Is this what is call 'hard reboot' when I restart the computer?
Maybe there was an automatic update in the background that I was not aware of when I pressed the Shut-down button. And this could have caused the Sudo file to be broken. The question is how are we to know that there is an automatic update in the background when the computer seems to be not shutting down?

---

