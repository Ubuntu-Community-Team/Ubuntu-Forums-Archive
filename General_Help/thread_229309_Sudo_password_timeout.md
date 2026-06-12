---
title: "Sudo password timeout"
date: 2006-08-04
forum: General Help
---

### Post by viciouslime on 2006-08-04
If you do something that requires your password, eg start synaptic, once you close it you are able to open it again, or any other administrative app that would normally require your password, without entering it. If you wait a while though, your password is required again, where do you change the amount of time allowed before you have to enter your password again? Also, is it possible to change it to once-per-session?

---

### Post by huygens on 2006-08-04
It is easy to change, but one small mistake and you might f*ck'd up your sudo parameter file and thus your ability to use sudo. In this case, you'll have to boot to recovery mode or using a live CD and fix the sudo parameter file.
So just do it if you feel confident with your skill in this regard, or if you know someone that could come and fix the situation for you.

What you need to do is tweak the parameter **passwd_timeout** in the sudoers file (inside directory /etc/). BEFORE RUNNING TO EDIT THE FILE, READ CAREFULLY BELOW. The unit of this parameter is in minute. So setting this parameter to 5 (as is the default) will give you a password timeout of 5 minutes.
There is 2 ways to edit the sudoers file, one safer way (but you need to know 'vi'), one mad way (potentially you could loose administrativ privilege and it could require that you reboot in recovery mode).[LIST]
[*]**the safer way**, you need to type in a terminal (Applications->Accessories->Terminal)[/LIST]```
sudo visudo
``` You will then be able to edit this file using vi. See what to modify below.
[LIST]
[*]**the mad way**, you need also to type in a terminal (there is a graphical way, but I cannot recall it...)[/LIST]```
gksudo gedit /etc/sudoers
``` [LIST]
[*]**What to modify?**[/LIST]You need to find a line starting with "Defaults". If there isn't, you add a line and write this:
[FONT=Courier New]Defaults passwd_timeout=10[/FONT]
If there is already one and there is at least one parameter, you can add passwd_timeout at the end separating from the rest by a comma like in this example:
[FONT=Courier New]Defaults syslog=auth,passwd_timeout=10[/FONT]

If you don't feel expert enough, don't hesitate to leave it as it is now, 5 minutes can feel combursome, however not having administrativ privilege is by far worse!

Huygens

---

### Post by Ramses de Norre on 2006-08-04
The safe way to edit sudoers with gedit is ```
export EDITOR=gedit && sudo visudo
```

---

### Post by huygens on 2006-08-04
> **Ramses de Norre said:**
> The **safe way** to edit sudoers with gedit is: export **EDITOR=gedit** [...]
Is this set-up for Ubuntu? I thought it might break security and was not recommended...

---

### Post by viciouslime on 2006-08-04
Thanks very much for your help huygens! Just one thing, why is the mad way mad? This is how I would edit all my other settings files, what's different about this one? Thanks.

---

### Post by huygens on 2006-08-04
> **viciouslime said:**
> why is the mad way mad?


For other files, this way is a good way to edit them. However, for the particular purpose of sudoers, it is different (and once I tasted the difference, it was bitter)
If you modify sudoers and make a mistake (forgot a comma somewhere for instance), sudo might not understand the sudoers file because of a parsing error. Then you do not have sudo access, meaning on Ubuntu you cannot do anything anymore related to administrativ tasks. Each time it should prompt you for a password, it will be unable to verify if you are allowed or not to launch the file. That's why you need to go in recovery mode or use a live CD and correct the sudoers file then.

By using visudo, it does several things making the change safer:[LIST=1]
[*]it is locking the file, so that concurrent modification is not allowed. Only one person (if this person is also using visudo) can edit the file at once,
[*]it is performing some basic consistency checks. Thus, if visudo cannot parse the file, it will warn you and ask you if you would not like to review once more your changes before committing (saving) them.[/LIST]This is why it is safer, and the other way is mad ;) (or crasy if you prefer, but I did not want to write crasy, as you or someone else having the same problem might dare to be crasy :) )

Huygens

---

### Post by viciouslime on 2006-08-04
Lol thanks a lot huygens. That answers my next question too. I was going to ask once I have the modified file, if I reinstall ubuntu, can I just copy the modified file over the new one like I could with say smb.conf. I guess I can since really that file behaves like all others, but it's just very dangerous to edit hence you should really use visudo as a precautionary measure...right?

---

### Post by ifokkema on 2006-08-04
> **viciouslime said:**
> I guess I can since really that file behaves like all others, but it's just very dangerous to edit hence you should really use visudo as a precautionary measure...right?
Yup :)

---

### Post by Ramses de Norre on 2006-08-04
> **huygens said:**
> Is this set-up for Ubuntu? I thought it might break security and was not recommended...

Why would it be insecure to use gedit as editor if you like that more? You still use visudo, you only change the editor visudo uses. Visudo is in no way bounded to vi, it works with every editor (by default it uses nano and not vi), this editor is set by the EDITOR variable which you can change with the command I showed.

---

### Post by viciouslime on 2006-08-05
Ahh, that makes sense. I thought it looked like nano when I was using it.

---

### Post by huygens on 2006-08-06
> **Ramses de Norre said:**
> Why would it be insecure to use gedit as editor if you like that more? You still use visudo, you only change the editor visudo uses. Visudo is in no way bounded to vi, it works with every editor (by default it uses nano and not vi), this editor is set by the EDITOR variable which you can change with the command I showed.
It is not that you use gedit :) but I have read somewhere I cannot recall :( that allowing the use of the EDITOR env. variable is the insecure stuff... As a user could set EDITOR to a program that is not an editor.
Anyway, I never understood why because, if you have anyhow the right to modify the file, why is it insecure if EDITOR points to a script rather than to a text editor? Perhaps, it's to avoid viruses that could have set the EDITOR variable without you noticing, and thus changing it to gain access to your files once you authorised it...

Huygens

---

### Post by MarinaraOfDeath on 2006-08-06
The **safe** way to use gedit (or preferably kate, but why try to start a flame war here...) is 

```
sudo cp sudoers sudoers_backup
```

before even opening the file. Put a date on each backup if you're gonna be altering sudoers a lot.

---

### Post by MarinaraOfDeath on 2006-08-06
viciouslime, that's a cherry avatar!

---

### Post by viciouslime on 2006-08-07
cherry?

---

### Post by Ramses de Norre on 2006-08-07
> **huygens said:**
> It is not that you use gedit :) but I have read somewhere I cannot recall :( that allowing the use of the EDITOR env. variable is the insecure stuff... As a user could set EDITOR to a program that is not an editor.
Anyway, I never understood why because, if you have anyhow the right to modify the file, why is it insecure if EDITOR points to a script rather than to a text editor? Perhaps, it's to avoid viruses that could have set the EDITOR variable without you noticing, and thus changing it to gain access to your files once you authorised it...

Huygens

That makes sense.. I don't know whether the visudo command would let the script modify or save the sudoers file but if it does it is indeed pretty dangerous.. But still then is setting the EDITOR var just before using visudo more secure then using visudo without knowing the value of EDITOR ;)

---

### Post by huygens on 2006-08-09
> **MarinaraOfDeath said:**
> The **safe** way to use gedit [...] is 
```
sudo cp sudoers sudoers_backup
```

I have to disagree :oops: because:[LIST]
[*]OK you have a back-up, but
[*]If sudoers is incorrect after the modification with your editor, you cannot modify sudoers anymore, nor obviously can you restore the back-up..., why?
[*]Because, restoring the back-up would involve:```
sudo cp sudoers_backup sudoers
```This will fail! sudo will report a syntax error in the sudoers file and not granting you higher privilege. Thus, as a normal user you cannot overwrite sudoers, so the command will be rejected...
[*]Your only way out, it to boot in recovery mode (see prompt at boot time) or to boot on the Ubuntu live CD. Then you will be able to restore the backup or simply correct the modified sudoers file.[/LIST]So I would not recommend to someone not knowing how to use the recovery mode to directly edit sudoers with gedit. Anyway, even if you are a Linux guru, it is better to edit sudoers with visudo. You will avoid yourself an unecessary reboot of your computer to fix the file ;)

Huygens

---

### Post by huygens on 2006-08-09
> **Ramses de Norre said:**
> [...]But still then is setting the EDITOR var just before using visudo more secure then using visudo without knowing the value of EDITOR ;)

Good point :)

---

### Post by MarinaraOfDeath on 2006-08-10
huygens, su or logging in as root are different ways to accomplish the same goal. And there's always single/recovery mode/whatever you want to call it.

---

### Post by MarinaraOfDeath on 2006-08-10
Heck, if it comes to it, anyone running Ubuntu should have a live CD sitting around somewhere. Aside from the install CD, I keep a copy of Knoppix around for emergencies.

---

### Post by ifokkema on 2006-08-10
> **MarinaraOfDeath said:**
> Heck, if it comes to it, anyone running Ubuntu should have a live CD sitting around somewhere. Aside from the install CD, I keep a copy of Knoppix around for emergencies.
The Dapper install CD IS a Live CD :)
Can't get any better than that... :KS

---

### Post by Ramses de Norre on 2006-08-10
But knoppix is better in system resque purposes, I have one laying around here too ;)

---

### Post by ifokkema on 2006-08-10
> **Ramses de Norre said:**
> But knoppix is better in system resque purposes, I have one laying around here too ;)

Really? Well, since Knoppix has been around longer than Ubuntu, it's pretty logical, I guess. I never worked with KDE, so I'd even have to search for the terminal :)

Luckily so far, the Live CDs (Hoary/Breezy/Dapper) have always helped me out with everything.

---

### Post by Ramses de Norre on 2006-08-10
I never work with kde outside of knoppix neither ;) And the konsole icon is next to the menu icon, you can't miss it =)

---

### Post by huygens on 2006-08-10
Hello again,

It seems that instead of password_timeout, there is timestamp_timeout... In case, my first post did not help you, you could always try this method:

[http://doc.gwos.org/index.php/Change_default_timeout_in_sudo](http://doc.gwos.org/index.php/Change_default_timeout_in_sudo)

Huygens

---

### Post by huygens on 2006-08-10
Hello MarinaraOfDeath

> **MarinaraOfDeath said:**
> [...]su or logging in as root are different ways to accomplish the same goal.
Thanks, but I knew this already. So perhaps could you point me at the sentence I have written that made you thought I did not know that? Then, I could perhaps clarify it. As I am not a native English speaker, I probably turn sentence in ways not always clear.

Huygens

---

### Post by viciouslime on 2006-08-10
Your first response did help. This second link is also very useful however, thanks!

---

### Post by MarinaraOfDeath on 2006-08-12
Nah, huygens, I figured you knew it but weren't thinking of using an alternate approach to fixing a problem at that particular moment since you typed "sudo cp" (which only makes sense given that this thread is abot sudoers). Whereas I'm not at all shy about risking f'in up my system -- bring on root and/or windows registry hacking!

---

### Post by MarinaraOfDeath on 2006-08-12
> **ifokkema said:**
> The Dapper install CD IS a Live CD :)
Can't get any better than that... :KS

Oh, I agree. Aside form all the carping over whether making the install a live CD, I think that's really handy. But somehow Knoppix still seems ebtter for repair purposes (maybe just for the imprinting caused by having linux find your wireless for the first f'n time ever! :-D )

---

### Post by ifokkema on 2006-08-12
> **MarinaraOfDeath said:**
> Oh, I agree. Aside form all the carping over whether making the install a live CD, I think that's really handy. But somehow Knoppix still seems ebtter for repair purposes (maybe just for the imprinting caused by having linux find your wireless for the first f'n time ever! :-D )
LOL :)
Well, I guess that's two votes for Knoppix ;)
Next time I have to fix someone's messups, I will consider trying Knoppix in stead of the trusted Live CD :)

---

