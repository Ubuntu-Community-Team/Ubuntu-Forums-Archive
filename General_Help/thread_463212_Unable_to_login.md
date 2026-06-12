---
title: "Unable to login"
date: 2007-06-03
forum: General Help
---

### Post by joshier on 2007-06-03
I'm unable to login. tried ubuntu/wubi and my default windows login.

---

### Post by skezza on 2007-06-03
I have just tried Wubi for the first time on a laptop. Although its not essential i use it, i just wanted to give it a try. Three times i have had invalid username on the text based installer and it doesnt allow me to enter an alternative. It says the username should have lower case letters etc, which it does. I have tried 3 different usernames. What do you recommend i do?  is this common?

---

### Post by notquitemichael on 2007-06-03
just a suggestion, but if you use some more exciting charectors, noteabley ~ and @ in your password it may just be because your keyboard is mapped wrong (i.e. it thinks you've got an american keyboard when your british.) try typing in your password in the username box just to check it's writing right.

this ALWAYS happens to me after letting nvidia-settings save changes.

---

### Post by ago on 2007-06-03
When you installed wubi didn't you see this screen?

[img]http://cutlersoftware.com/ubuntusetup/wubi/en-US/screenshots/wubi-main.jpg[/img]

Whatever username/password you used there is what you have to use. Press alt+f2 just to check that the keyboard is ok.

---

### Post by skezza on 2007-06-03
i did, but even having entered a very simple username and password, i got invalid username on the text based installer. looks like im going to have to use the live CD by the looks of it :(

---

### Post by Vadi on 2007-06-03
Did you try 'ubuntu'?

---

### Post by ago on 2007-06-03
Do you see any other error message? Did you try to login from terminal (alt+f3)? Did you check that the keyboard is correct (type something in the terminal)?

---

### Post by MikeM709 on 2007-06-03
did you try it with and without caps lock?

---

### Post by skezza on 2007-06-03
yes but i tried ubuntu studio on this machine and it worked fine :) really well, in fact im on it right now.

---

### Post by Healer77 on 2007-06-04
Hi Skezza,

I experience the same. The installer halts, and I can't select another username.
This didn't occur in Test1. Didn't test in Test2.

Tried to change to another instance, and the keyboard works there (with Danish special characters).
I selected US English during installation.

Best regards

---

### Post by ago on 2007-06-04
Can you guys please try Wubi Test3?

I'll try to help but please use latest release.

---

### Post by ago on 2007-06-04
Make sure that you use the same username/pwd you entered in the dialog. Keep username and password simple with no white spaces.

[img]http://cutlersoftware.com/ubuntusetup/wubi/en-US/screenshots/wubi-main.jpg[/img]

If you do have issues, press Alt+F3 and try to login from there. See the logs in /var/log for any hint.

---

### Post by joshier on 2007-06-04
Shortly after I posted this, it worked with me, quite odd! maybe I done it wrong. Anyway, thanks for all your help.

---

### Post by Healer77 on 2007-06-04
Just tried again with Test3.
The installer still fails saying that my username is illegal, an I must create a new one.
I simply chose: afr
So no fancy stuff or anything... :)

When I select alt+F3 I get a Busybox shell. No need to login. I browsed through the logs, 
but none seemed to contain any useful info.

I also tried UbuntuStudio with the exact same result.
Lastly I tried to change my Windows locale to US English, but still nothing.

Any more thoughts?
All your help is greatly appreciated!

---

### Post by ago on 2007-06-04
If you get a busybox it means that some step failed. See if /home is mounted. See the logs in /media/host/wubi/lupin.log and /var/log/syslog

---

### Post by Healer77 on 2007-06-04
Hi again,

Must say.. This is isn't the easiest thing to do for a Windows-nerd like me. :)
But i managed to salvage the different logs you requested.
It does mount a /target/home, but I'm not sure if something else fails.
It looks like it has some problems regarding the creation of user-space.

I put the logs here: [http://www.sonicboom.dk/wubi/]("http://www.sonicboom.dk/wubi/")

Please take a look at them if you get the chance.
Thanks. :)

---

### Post by ago on 2007-06-04
> **Healer77 said:**
> Hi again,

Must say.. This is isn't the easiest thing to do for a Windows-nerd like me. :)
But i managed to salvage the different logs you requested.
It does mount a /target/home, but I'm not sure if something else fails.
It looks like it has some problems regarding the creation of user-space.

I put the logs here: [http://www.sonicboom.dk/wubi/]("http://www.sonicboom.dk/wubi/")

Please take a look at them if you get the chance.
Thanks. :)

Healer those are installation logs not normal boot logs. Did the installation complete at all?

---

### Post by Healer77 on 2007-06-04
Nope, It's in the installation phase i get the error: Invalid Username
Sorry if I wasn't clear. It seems that 2 threads has gotten mixed up somehow.
Don't know what happened... :)

It happens right after it tries to get an address from DHCP.

---

### Post by ago on 2007-06-04
> **Healer77 said:**
> Nope, It's in the installation phase i get the error: Invalid Username
Sorry if I wasn't clear. It seems that 2 threads has gotten mixed up somehow.
Don't know what happened... :)
I merged them I thought you meant login at normal boot

before rebooting from windows have a look at c:\wubi\install\preseed.cfg, see if the username line looks suspect, and if you get asked a username try to type another username.

---

### Post by shadow01 on 2007-06-05
Hi people, 

I also get that unable to login...think it can't be the username/pw cause I used the same as on an other computer...

After getting "invalid user", I hitted "ESC" and got to the installer menue...there I tried to configure user/pw, and got error: couldn't unmount hda1 ... don't know what could be the problem...

I have 2 partitions, c: with windows as FAT 32 and d: as NTFS ... I have the wubi-installer and the disc-image on  d: and tried to install to d:\wubi ... tried it 3 times, shut down windows manually, all times the same error...
Oh, and **D:**\wubi\install\preseed.cfg doesn't exist...

Any help would be appreciated...

THx in advance,
shadow01


Edit: Btw if it is helpfull: the computer is an acer aspire 1350

---

### Post by ago on 2007-06-05
You need uninstall then run wubi again, preseed is deleted every time you install. Try to enter a different username/password and see if it works. You can check d:\wubi\install\pressed.cfg before rebooting

---

### Post by shadow01 on 2007-06-05
wow, fast reply, thanks...

now I found the preseed.cfg ... it sais:
(don't mind to post name cause it's only temporarily   -   username=pequet ; pw is a combination of 8 numbers-only, no letters,caps,etc.)

...
#to create a normal user account.
d-i passwd/user-fullname string pequet user
d-i passwd/username sting pequet
...

I wonder about that user-fullname string ... the windows user name, which is offered by the installer first is name [space] surename, what is said to not work because of the space ... I mean not that the windows-name is imported for any reasons, even if i change it to be pequet for wubi?

thx, shadow

PS: sorry for my bad english...

---

### Post by camericob on 2008-11-18
> **Healer77 said:**
> Hi Skezza,

I experience the same. The installer halts, and I can't select another username.
This didn't occur in Test1. Didn't test in Test2.

Tried to change to another instance, and the keyboard works there (with Danish special characters).
I selected US English during installation.

Best regards

made the download (ok) but unable to login. my first time! keeps asking for user name and password and telling me they are wrong. i can´t say is userfriendly system

---

### Post by ago on 2008-11-18
Make sure username and passwords are what you expect. You can type the password in a clear text field (the username...) to check that there are no unexpected chars (because of wrong keyboard layout). The username used is spelled in the wubi log within windows, in your user temp folder.

---

