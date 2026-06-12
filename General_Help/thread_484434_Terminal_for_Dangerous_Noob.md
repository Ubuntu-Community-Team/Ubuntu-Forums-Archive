---
title: "Terminal for Dangerous Noob"
date: 2007-06-25
forum: General Help
---

### Post by Anzan on 2007-06-25
Oh hai

I am a complete noob in Linux. My twenty years of experience in Macs and MS will do me no good here.

I would like to learn Bash but the virtual terminal application that is the default in Ubuntu sets me as root.

If I use it to go through various instructional manuals I could do some real damage.

Can someone tell me:

Is there a terminal I can download that will not set me as root so that I can futz about harmlessly? 

Or can I use the Root Terminal app to set myself as a powerless user without, oh say, making that permanent?

Also:

Any recommendations or advice?

Thanks for your time.

---

### Post by merlinus on 2007-06-25
Why not use the regular terminal?  There you are user, unless you prefix commands with sudo or gksudo, or su.

Or have you logged in as root?

-merlin

---

### Post by tgm4883 on 2007-06-25
The terminal shouldn't give you root access unless you sudo a command, or do su -

---

### Post by Anzan on 2007-06-25
Ah.

It has # which means "root" (I think) and I have to use my password to use the terminal but I can't do Bad Things unless I use the sudo prefix?

Great. Thanks.

---

### Post by euler_fan on 2007-06-25
> **Anzan said:**
> Ah.

It has # which means "root" (I think) and I have to use my password to use the terminal but I can't do Bad Things unless I use the sudo prefix?

Great. Thanks.

No. If it has a $ prompt then you have to use sudo and your password to, as you put it, "Do Bad Things". If you have the # prompt you can do bad things at any time. Which version of Ubuntu are you using? In X- and U-buntu the default terminal is as a regular user with the $ prompt. You should really get the default terminal back (not sure how to do that) and get rid of the one you are using.

Your caution is commendable. I would advise getting rid of any terminal that says "as root" after it and getting the ones that don't. Try the Add/Remove Programs program to get another terminal.

---

### Post by Anzan on 2007-06-25
Thanks, euler_fan.

I'm using 7.04.

The tooltip popup (from the icon) says Root Terminal and uses gksu to ask for the password.

And it does show # rather than $.

I'll look around for another terminal app but I would appreciate suggestions from you or anyone.

---

### Post by Anzan on 2007-06-25
Ah!

I found another terminal app that has $ already installed.

A Very Unixy Person kindly helped me install Ubuntu so that my widescreen monitor had the right resolution. The Root Terminal must have been what he was using.

Thanks all.

---

### Post by ipx on 2007-06-25
Try this:
- Press ALT + F2
- Type 'gnome-terminal'

What do you get? That should launch the regular terminal in ubuntu, and should not start as root (unless you are logged in as root?).

You got your own user, right?

(Actually, i finally got the thumb out of my *** and registered just to answer this post. Dont worry, i'll stay. ;))

---

### Post by Anzan on 2007-06-25
Thanks very much, ipx, but all is now well.

Obviously, we need people like you to post so if my noobinosity helped with that, I'm glad.

---

