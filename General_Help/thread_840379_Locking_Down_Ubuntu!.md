---
title: "Locking Down Ubuntu!"
date: 2008-06-25
forum: General Help
---

### Post by CD Baric on 2008-06-25
Hi.

I have a client that is constantly altering his Ubuntu installation and then calling me in a panic at month's end when he must finish his assignment and turn in his work.

I have tried to be patient and helpful but I have had enough - how do I lock down his desktop so he can't alter/wreck it?

Thanks,

CD Baric

---

### Post by dracayr on 2008-06-25
I don't think there is a possibility other than removing him from sudoers and changing the root password...

dracayr

---

### Post by bodhi.zazen on 2008-06-25
Even then ...

The only way is to use the alternate cd and install into an encrypted partition and do not give the user either admin access or the encrypted password.

Mind you this makes it difficult to boot but anything short of that is easily defeated with a live CD.

Best contract with the user, you will sys admin if and only if he/she does not play with system files.

Better, what about installing something like virtualbox or VMWare so the user can play in a safe environment without affecting the primary system ?

---

### Post by Cotopaxi on 2008-06-25
"Mind you this makes it difficult to boot but anything short of that is easily defeated with a live CD." ](*,)

3 thoughts:

1) If CD Baric enters the Computer's Boot Menu, sets up a password for accessing the boot menu and disables booting from CD, could that work?

2) Within Ubuntu: can CD Baric disable the access of the Client to the CD ROM Drive?

3) Charge the client such a hefty fee for this "Emergency System Rescue" that he will think it over twice before he ever screws up again! :cool:

---

### Post by CD Baric on 2008-06-25
Thank you all for replying.

I will elaborate - the client in question constantly changes parameters like deleing panels, deleting panel items like his menu system and pager applet.

He is a very creative writer and posts columns every month for a national magazine but the fellow is a complete Ludite who can't stop fiddling.

I am not concerned about CD access becausse he is incapable of the depth of tecnolog BUT he did manage to turn off OpenOffice Word visible text area markings.

I have fined him hideously for his transgressions but he seems incapable of reform. (He had s similiar problem with XP and that is how I got him - his Windows guy finally told him to get lost.

Is their any way to safeguard his desktop while still allowing him to write?

I may be forced to move him to KDE.

Thanks againg for your help.

CD Baric

---

### Post by bodhi.zazen on 2008-06-25
You can check these links :

    [http://lifehacker.com/software/featured-linux-download/timevault-time-machine-for-linux-275399.php](http://lifehacker.com/software/featured-linux-download/timevault-time-machine-for-linux-275399.php)
    [https://launchpad.net/timevault/+download](https://launchpad.net/timevault/+download)

    Dirvish : [http://www.dirvish.org/](http://www.dirvish.org/)

    Others : [http://ubuntuforums.org/showthread.php?t=723535](http://ubuntuforums.org/showthread.php?t=723535)

Or , even easier, set up a working profile, back it up ...

Then sudo cp -R /home/backup/* /home/username

Or tar excluding a data directory, or rsync ...

---

### Post by ibuclaw on 2008-06-25
For locking down the desktop you may also consider looking into the gconf-editor (Press **Alt+F2"** and type in **gconf-editor** in the textbox.) and enabling this value:

**/apps/panel/global/locked_down**

It will lock down any altering of the gnome panels.

Regards
Iain

---

### Post by sdennie on 2008-06-25
Along with tinivoles suggestion, within gconf-editor, you can also look in /desktop/gnome/lockdown and lock various other operations of the machine.

---

### Post by Zorael on 2008-06-25
*"If someone has physical access to your computer, it's no longer yours."*

I don't know whose quote that is (Gates? Intel/IBM developer?), but it's very true.

---

### Post by CD Baric on 2008-06-25
That's very good - Thanks.

That gives me lots of ideas.

He could email me and request changes. ;)

CD Baric

---

### Post by CD Baric on 2008-06-25
That looks exactly what I am looking for.

Thanks,

CD Baric

---

### Post by CD Baric on 2008-06-25
Even better!

Thanks everybody for answering - I have been given lots to think about.

Best regards,

CD Baric

---

