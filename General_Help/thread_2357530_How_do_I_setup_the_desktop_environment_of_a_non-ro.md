---
title: "How do I setup the desktop environment of a non-root account?"
date: 2017-04-03
forum: General Help
---

### Post by webmiester on 2017-04-03
Hi guys,

I am trying to setup a terminal for people in the library to use.  Here is the thing: I want it to look like Windows 10 just so that the children using this won't be too "alienated" with the Ubuntu interface.

Here is the clincher:

I made an account with no root privileges for them to use.  I called it "Libraryuser"...  Now when I log into Library user and try to follow the commands in this link: [http://www.noobslab.com/2014/04/make-your-ubuntulinux-mint-look-like.html](http://www.noobslab.com/2014/04/make-your-ubuntulinux-mint-look-like.html).. they don't work because the account doesnt have root privileges.

So here are my questions:
1) How do I use temporary root privileges from the terminal?  I tried "su root" but it doesn't work.  I also tried "su Proto" (Proto is the root account), but it also doesnt work :(  What am I doing wrong?

2) Is there a way to setup the desktop of a non-root user from the root account?

Thanks so much

---

### Post by izznogooood on 2017-04-03
You use sudo.

"sudo apt update" etc...

[https://linux.die.net/man/8/sudo](https://linux.die.net/man/8/sudo)

For permanent root "sudo su"

---

### Post by SeijiSensei on 2017-04-03
Ubuntu doesn't support root logins by default, in contrast to RedHat flavors, preferring instead to use the sudo mechanism: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Only the user you created during installation is granted sudo privileges.  So to do administrative tasks, you need to run as that user.  You most definitely do not want the LibraryUser account to have admin privileges for obvious reasons.

You can add users to the "sudoers" list, but I wouldn't recommend it, especially on a public machine like this one.  And make sure your account with admin privileges has a strong password.

If you have a lot of experience, you can get to a root shell with the command "sudo su".  If you're just setting out with Linux, I strongly recommend sticking to the sudo model.

Also I'd take a look at Kubuntu if you want something more "Windows-like."  There's also this KDE theme: [https://store.kde.org/content/show.php/Windows+10+Plasma+Theme?content=174453](https://store.kde.org/content/show.php/Windows+10+Plasma+Theme?content=174453)

Another option is "kiosk mode:" [https://help.ubuntu.com/community/KioskMode](https://help.ubuntu.com/community/KioskMode)

> 2) Is there a way to setup the desktop of a non-root user from the root account?
Configuring a user's desktop should not require any root privileges. That article you linked to only appears to use sudo to install software.  Do that with the privileged account.  You should be able to do everything else from the LibraryUser account after the software is installed.

---

### Post by Habitual on 2017-04-03
alienated is a strange word to use.
Implies they know Windows?

I'm always surprised by what kids know and how they got to know it.

---

### Post by SeijiSensei on 2017-04-03
Actually I think kids these days aren't really locked into a particular desktop metaphor.  Just moving from PCs to smartphones and back again makes them less constricted by such conventions.  Personally I have a hard time trying to use Mac OSX which I find pretty unintuitive despite the hype from Cupertino.

---

### Post by webmiester on 2017-04-09
> **Habitual said:**
> alienated is a strange word to use.
Implies they know Windows?

I'm always surprised by what kids know and how they got to know it.

Yes, unfortunately.  The school is required by the government to teach Windows OS.  Its really irritating.  The government regulations do not actually state any particular operating system, but the government exam which certifies these kids will be using Windows Server.  So what gives?  I tried to come up with a "Windows simulator" using Linux, but since their government exam is how to install, setup, and use Windows Server, linux really won't do, unless I want to be blamed for their poor performance in the examinations in the end.

So the best I can do is at least setup their library computers to run on linux, then have those look like windows, hahaha.

Anyway, thanks so much for the inputs.  I finally figured out how to do it by using the guess account, and making the guess account have the look and feel I wanted :).

Thanks so much!

> **SeijiSensei said:**
> Actually I think kids these days aren't really locked into a particular desktop metaphor.  Just moving from PCs to smartphones and back again makes them less constricted by such conventions.  Personally I have a hard time trying to use Mac OSX which I find pretty unintuitive despite the hype from Cupertino.

Yes, I dislike the MacOSX too.  It just doesnt feel right to me.

---

### Post by SeijiSensei on 2017-04-09
> **webmiester said:**
> Anyway, thanks so much for the inputs.  I finally figured out how to do it by using the guess account, and making the guess account have the look and feel I wanted.
So if you're logged into the guest account, can you make changes to the desktop?  If so, then you're not done yet.  You need remove write privileges from the hidden "dot" files and directories in the guest account like the .gnome and .config directories and the files they contain.

---

### Post by webmiester on 2017-04-20
> **SeijiSensei said:**
> So if you're logged into the guest account, can you make changes to the desktop?  If so, then you're not done yet.  You need remove write privileges from the hidden "dot" files and directories in the guest account like the .gnome and .config directories and the files they contain.

Yes, that would be ideal.  The current setup though is that  the desktop will revert to their old selves after bootup.  If I restrict write privileges, does this mean the kids wont be able to download stuff they find on the internet?  I want them to be able to download their files, and save them on their usb.

Your suggestion is very good.  I think I got some instructions on a different thread.  Ill try those. thanks!

---

