---
title: "Kernel update: Keep pulling my hair out"
date: 2006-09-15
forum: General Help
---

### Post by PereUbu on 2006-09-15
Argghhhhhhhhhhhhh!!!!!!!!!!!!!

This is so frustrating..... ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) 

Well, I'm also a victim of the last kernel-update.

I think I've tried every possible solution described here in the forums. 

I have:
- followed the steps in these posts     [http://www.ubuntuforums.org/showthread.php?t=213420](http://www.ubuntuforums.org/showthread.php?t=213420)
[http://www.ubuntuforums.org/showthread.php?t=257459](http://www.ubuntuforums.org/showthread.php?t=257459)
- changed driver from nvidia to nv in xorg.conf
- restored my oldest xorg.conf
- downgraded to .23 kernel
- removed all packages associated with nvidia-glx, restricted modules etc.
- apt-get update/upgrade/dist-upgrade

But still no X! Have I forgot something? Why are GDM not showing up?

I'm about to give up and start looking for another distro. I've been using Ubuntu since Warty Warthog 4.10. Now I'm trying to convince myself NOT to wipeout my hda1 and install Debian instead. Dang I'm dissapointed. pewwwww (the sound of steam being let out)

Please help me! I'm about to sink into a deep distro depression.

/PereUbu (pardon my expressive language)

---

### Post by David Corrales on 2006-09-15
I installed the .25 kernel along with it's restricted modules and could boot back into X with no problems. Then I re-upgraded to .26 and it's fine now.
I do have to tell that dapper has 2 strikes so far in such little time... where's QA :(?

---

### Post by PriceChild on 2006-09-15
Have you definately installed linux-arch (e.g. linux-386)?

If so... then we could try to reconfigure X:

sudo dpkg-reconfigure xserver-xorg

If you are unsure... don't change it. There will hopefully be some obvious fault.

(A backup of your xorg.conf will be created to revert to)

---

### Post by PereUbu on 2006-09-15
Thanx alot for pointing out the obvious solution, PriceChild!

I'm a happy man again. You see, I did not think it would solve my problem because I restored the original backup of the xorg.conf file. But I was wrong.

Ubuntu is not that bad after all, and this community is simply the best.

Cheers!
/PereUbu

---

### Post by PriceChild on 2006-09-15
No problem.

Enjoy yourself

---

### Post by PereUbu on 2006-09-16
Hi there! I'm back again.

I guess I'm back on square one again. No X after booting my PC :( 

So I tried install the XFCE desktop. And it went fine, sort of... Still no graphical login after booting, but I can now login through the console and when I type startx the XFCE desktop pops up. A bit quirky but at least I have a GUI (XFCE is a very nice desktop by the way).

That lead me to the assumption that it might be something wrong with GDM so I installed KDM and set it as default. KDM gives me an error message about not finding the themes folder, but I'am  now able to login to the gnome desktop again. Still a bit quirky, but I think I will get there eventually.

What to do next I don't know. Maybe you know the solution?


Best regards!

PereUbu

---

