---
title: "Custom Boot Wanted"
date: 2007-09-02
forum: General Help
---

### Post by mahalos on 2007-09-02
here's the deal.....

I'm building an arcade machine for my son, and whilst i've done several machines before they've always been windows based. Having converted to Linux 6mnths ago i thought i'd base the next machine on Ubuntu.

I'm using SDLmame, and Wahcade as a frontend. I have these two apps running fine, now i just need to make the boot sequence pretty. What i mean by 'pretty' is from the time I press the on button i only want to see the Usplash (which i will change to something more appropriate) and then from there straight into Wahcade.

So i need to figure out how to remove the  "loading grub" text, the machine is set to auto login with no splash screen so that's fine.  How do i stop the desktop from loading? and have wahcade load instead?

Any help is always appreciated, and go easy on me as i still considered myself a noob:)

---

### Post by ddrichardson on 2007-09-02
Not totally familiar with some aspects of Ubuntu yet, but it involves changing what happens at the runlevel that starts GDM and setting the machine to single login mode.

At the current runlevel gdm is started, what you'll need os to startx instead and use an .xinitrc script that has a single entry for wahcade, without an & after it. This way when wahcade exits the display is also exited.

---

### Post by mahalos on 2007-09-02
Thanks for the reply, 

I've found the default .xinitrc script and had a look at it.  It looks like this
```
#!/bin/sh
# $Xorg: xinitrc.cpp,v 1.3 2000/08/17 19:54:30 cpqbld Exp $

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
. /etc/X11/Xsession
```


Do i just need to create another one that looks like this

```
#!/bin/sh
# $Xorg: xinitrc.cpp,v 1.3 2000/08/17 19:54:30 cpqbld Exp $

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
. /usr/games/wahcade
```

---

### Post by mahalos on 2007-09-02
So i managed to track down this guide, which was very helpful indeed!

[https://help.ubuntu.com/community/CustomXSession]("https://help.ubuntu.com/community/CustomXSession")

so now i'm booting straight into wahcade. Although i have to now figure out how to get rid of the mouse      pointer that appears before wahcade loads and also the grub loading text. Any tips?

---

### Post by ddrichardson on 2007-09-03
I can-t think of a way to get rid of the mouse - it's always been the way X starts, even in its most basic config - grey screen, mouse, first program. As for the grub loading text, if you mean the "grub booting in..." then just change the timeout value to zero in menu.lst

---

### Post by mahalos on 2007-09-03
what i'm looking for now is a program to edit an X11 cursor theme so i can either make them black or ridiculously small. Not that i'm having much luck finding an app.

The grub text i'm talking about is 

starting grub stage 1.5
grub loading, please wait

I have the timeout set at zero.  Buggered if i know how to stop that from appearing

---

### Post by ddrichardson on 2007-09-03
I don't think you can without recompiling it. It can't really be much more annoying than the BIOS boot screen though.

If you poke about in the man pages for xinitrc and startx then I'm sure there is a way to change the pointer to text symbols - perhaps a period would suffice. However someone may know more about this than me.

---

### Post by shad0w_walker on 2008-02-08
Reviving a fairly dead thread here but I saw the thing about hiding the cursor and couldn't help but post.

Have a look into unclutter, it's in the repos and can be setup to hide the cursor immeadiately upon start and if you are running a custom X session it should be starting quick enough to hide the cursor almost entirely.

---

### Post by Tanno on 2008-02-20
What about uninstalling and removing the mouse if you don't need it?

Don't ask me how....I'm still new to Linux as it is.

---

### Post by shad0w_walker on 2008-02-20
Why would you want to remove support for the mouse? Using unclutter is the better option as it hides the cursor, is a very small program and if you ever need to use the mouse again for whatever reason then you just kill the program and it is available. No need to jump through hoops and do really unneeded things.

---

