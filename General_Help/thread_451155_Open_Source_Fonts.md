---
title: "Open Source Fonts"
date: 2007-05-22
forum: General Help
---

### Post by JacobRogers on 2007-05-22
Where is a good place to find fonts that are totally free and can be distributed or changed without any legal mumbo jumbo.  I have Times New Roman installed on my Ubuntu machine and I got it from some sort of "get apt ms font" something like that, but after doing some research I think that my possession of these fonts might not be totally legal.

I'm also looking for a Times New Roman alternative I could recommend to students without MS Word that is similar but free so I don't get in trouble for advocating the illegal distribution of a copyrighted font.

I think Open Office comes with a font family called "Nimbus" but I found them to be very dissatisfactory, hard to read, and erratically spaced.

Thanks for all of you guys patients and help.

---

### Post by linuxwizard on 2007-05-22
Look at the links at the bottom of this page. Maybe something there that will help you.
[https://help.ubuntu.com/community/FontInstallHowto](https://help.ubuntu.com/community/FontInstallHowto)

---

### Post by B00R4dL3y on 2007-05-22
If you're looking for more fonts you can try [dafont.com]("http://www.dafont.com/").  There's a pretty good selection there.

---

### Post by coffeecat on 2007-05-22
I believe Red-hat's liberation fonts will be useful to you. Go to [https://www.redhat.com/promo/fonts/](https://www.redhat.com/promo/fonts/) and download the tar.gz file, unpack it and install in the normal way. You'll see that Liberation Serif is a substitute for Times New Roman. The fonts are still in development - see [http://www.linux.com/article.pl?sid=07/05/16/1318240](http://www.linux.com/article.pl?sid=07/05/16/1318240) for the full story.

Worth keeping an eye on I should think.

---

### Post by JacobRogers on 2007-05-22
> **coffeecat said:**
> I believe Red-hat's liberation fonts will be useful to you. Go to [https://www.redhat.com/promo/fonts/](https://www.redhat.com/promo/fonts/) and download the tar.gz file, unpack it and install in the normal way. You'll see that Liberation Serif is a substitute for Times New Roman. The fonts are still in development - see [http://www.linux.com/article.pl?sid=07/05/16/1318240](http://www.linux.com/article.pl?sid=07/05/16/1318240) for the full story.

Worth keeping an eye on I should think.

Those are really quite nice, thank you.  I made this little thing in Open Office so others can see what Liberation Serif looks like next to Times New Roman.

[IMG]http://i21.photobucket.com/albums/b270/zerokey2003/font.jpg[/IMG]

Pretty good at size 12.  I did notice that after about size 20 Liberation starts to look less than par, but that's not important for my purposes.

Do I understand that I'm free to host and distribute these fonts totally legally without having to link to Red Hat or anything?  Not that I wouldn't link back to them out of gratitude, but I'm just trying to figure out if I _have_ to.

I've said it before and I'll say it again that this Ubuntu community is the best in my opinion.

Edit: I've been playing more and I think that my negative comment earlier was because of my eyes being tired.  Liberation Serif looks fine scaled above 20.  I wonder if this will make it into Ubuntu by default.

---

### Post by coffeecat on 2007-05-22
> **JacobRogers said:**
> Do I understand that I'm free to host and distribute these fonts totally legally without having to link to Red Hat or anything? 

From the RedHat link:

> You are free to use these fonts on any system you would like. You are free to redistribute them under the GPL+exception license found in the download. Using these fonts does not subject your documents to the GPL--it liberates them from any proprietary claim.Sounds like you should be fine, but IANAL (as they say). ;)

But bear in mind that they are still working on them. See the comments about hinting in certain font sizes in the second link.

---

### Post by JacobRogers on 2007-05-22
I asked that question before totally reading the article.  Such a duff I made of myself.  Thanks and I think I'm overly excited about these fonts because bad looking fonts has been my main reserve about Linux since I first tried it in 1999.

---

### Post by coffeecat on 2007-05-22
> **JacobRogers said:**
> bad looking fonts has been my main reserve about Linux since I first tried it in 1999.

The default on-screen font rendering in most (but not all) Linux distros is my personal dislike. I hesitate to mention this because the pros and cons of font rendering can induce flame wars that rival the intensity of Gnome v KDE and emacs v vi. :)

You may know this already, but if you've never seen the effect of autohinting on a LCD monitor, try this:

'sudo dpkg-reconfigure fontconfig-config'

Select autohinting and leave the defaults in the other two questions. You'll only see the difference when you've restarted the xserver. To get the full 'my desktop fonts look better than an Apple Mac' effect, use Verdana (a Microsoft font - sorry) or Dejavu Sans for everything except fixed width  in Font Preferences. Offhand, I don't know whether the dejavu fonts come with Ubuntu (I'm in Gentoo at the moment) but if you've not come across the dejavu set, this is something else you could investigate.

If you don't like autohinting, simply run the command again and switch it off.

---

