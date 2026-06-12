---
title: "Gnome to KDE help?"
date: 2006-11-05
forum: General Help
---

### Post by civint on 2006-11-05
I have been browsing the forums for posts about switching to KDE (as I wish to try it out, I have heard tell of it being slightly less stable than Gnome, although I feel that may be some gnome fanatics bashing an 'opposing' DE).
I understand the bit about 
"sudo aptitude install kde (or kubuntu-desktop-which would be better?)"

However, if I find out I want to keep KDE instead of gnome, would I simply be able to run 

"sudo aptitude remove gnome (or would that be ubuntu-desktop?)"

And be left with a KDE desktop environ? (I only want one, because I suffer from chronic tiny Hard drive-itus:( )


On another and totally off the point level--is perl a good place to start if I'm interested in programming?

---

### Post by justifier on 2006-11-05
firstly run 

sudo apt-get remove ubuntu-desktop 

reboot

in the command that u will get run the install command 

to save space and confusing the machine

---

### Post by NeoLithium on 2006-11-05
> **civint said:**
> I have been browsing the forums for posts about switching to KDE (as I wish to try it out, I have heard tell of it being slightly less stable than Gnome, although I feel that may be some gnome fanatics bashing an 'opposing' DE).
I understand the bit about 
"sudo aptitude install kde (or kubuntu-desktop-which would be better?)"

However, if I find out I want to keep KDE instead of gnome, would I simply be able to run 

"sudo aptitude remove gnome (or would that be ubuntu-desktop?)"

And be left with a KDE desktop environ? (I only want one, because I suffer from chronic tiny Hard drive-itus:( )


On another and totally off the point level--is perl a good place to start if I'm interested in programming?

Well, to install KDE; the best way on ubuntu is to ```
 sudo aptitude install kubuntu-desktop 
```

---

### Post by aysiu on 2006-11-05
Kubuntu is perfectly stable, but I think you'd be better off installing *kde-core*.

The command ```
sudo apt-get remove ubuntu-desktop
``` will not remove Gnome or Ubuntu.

And the command ```
sudo aptitude remove ubuntu-desktop
``` won't remove Gnome unless you installed Gnome with the command ```
sudo aptitude install ubuntu-desktop
```

When you say you suffer from chronic tiny hard drive-itus, how small are we talking about? When I had Xubuntu, Ubuntu, and Kubuntu installed on my hard drive, along with other other programs, I used about 3.5 GB of space. Is your hard drive smaller than that?

---

### Post by civint on 2006-11-05
will "sudo-apt get remove ubuntu-desktop" fully remove the gnome desktop environment, as I have heard tell that it is a meta package (i think) and so with apt-get remove i would only be removing the links (again, i think)?

---

### Post by aysiu on 2006-11-05
> **civint said:**
> will "sudo-apt get remove ubuntu-desktop" fully remove the gnome desktop environment, as I have heard tell that it is a meta package (i think) and so with apt-get remove i would only be removing the links (again, i think)?
It will remove nothing.

*ubuntu-desktop* is a pointer to the default packages in Ubuntu. If you remove it with *apt-get*, only the pointer will be removed.

If you had installed it with *aptitude*, an *aptitude remove* would remove it, but if you installed it through a regular installation (using the Desktop CD or Alternate CD installer) or through *apt-get*, that command will remove only the pointer.

---

### Post by civint on 2006-11-05
so the only way to switch completey to KDE would be to get a fresh install of Kubuntu? as I installed gnome ubuntu from the cd....

---

### Post by aysiu on 2006-11-05
> **civint said:**
> so the only way to switch completey to KDE would be to get a fresh install of Kubuntu? as I installed gnome ubuntu from the cd....
No.

You can install Kubuntu using this tutorial:
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

and then remove Ubuntu using this tutorial:
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by civint on 2006-11-05
Thanks alot for that aysui, I really appreciate that, and you seem to be an expert on these things (you pop up in every bit of background reading I do b4 a post!). So i just have to run that long bit of apt-get remove in oprder to remove the gnome desktop environment? (just a check) and then I will be left with a Pure KDE desktop....*sigh* :rolleyes:

And just a quick question again, is perl a good language to start off learning code (etc)?

Lol thanks again for helping a n00b

---

### Post by aysiu on 2006-11-05
Please keep in mind there are two "pure KDE" tutorials--one is for Edgy and one is for Dapper, and they *are* different.

I don't know anything about Perl or coding. I'm not a programmer. But someone else may be able to help you with that.

---

### Post by ckonrad on 2006-11-05
> **civint said:**
> Thanks alot for that aysui, I really appreciate that, and you seem to be an expert on these things (you pop up in every bit of background reading I do b4 a post!). So i just have to run that long bit of apt-get remove in oprder to remove the gnome desktop environment? (just a check) and then I will be left with a Pure KDE desktop....*sigh* :rolleyes:

And just a quick question again, is perl a good language to start off learning code (etc)?

Lol thanks again for helping a n00b


try the ruby programming language at [http://www.ruby-lang.org/en/](http://www.ruby-lang.org/en/) its a good begining language.

---

### Post by civint on 2006-11-06
Thanks a lot you guys. This reminds why I love ubuntu (or Kubuntu now as I have switched, and I love the feel of KDE, and will probably stick with it). Kudos to all who helped me.

---

### Post by civint on 2006-11-06
I just tried to do the gnome 'purge', and it came back with this error message 

> (Reading database ... 77202 files and directories currently installed.)
Removing scim-gtk2-immodule ...
/var/lib/dpkg/info/scim-gtk2-immodule.postrm: line 8: /usr/sbin/update-gtk-immodules: No such file or directory
dpkg: error processing scim-gtk2-immodule (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 scim-gtk2-immodule
E: Sub-process /usr/bin/dpkg returned an error code (1)


actually, scratch that, I just re-read the message and it explained itself. how embaressing.........it not there so cannot be removed. it just looked like a scray problem. reading teh error message again may help next time.......

---

### Post by tylerjames on 2006-11-08
python is good language to play with as well...
I use a lot of Java at school and I keep longing for some of the clean functionality provided by python.... plus you can try out code quickly with the interactive mode

python is in the repositories
official site is [http://www.python.org]("http://www.python.org")

---

### Post by GTonizuka on 2006-11-10
hello guyz,
i have a different problem but quite related to subject, i tried to switch from gnome to KDE and to do this, i have installed KDE from synaptic package manager and as i saw that everything was working perfectly, i removed all gnome packages again with spm. (yes, i did not checked forums before i do that(*,) ) it has removed also some primitive packages and now, i can not get into the xwindow (namely, KDE)]

now will it be sufficient to use:

sudo aptitude install ubuntu-desktop

to get my desktop back (KDE of course :) ) or my case is worse than i think?
(i cannot try anything at the moment cos i am at work right now)

one additional minor question:
isn't it strange that gnome has removed all necessary packages that has also been used by KDE?

---

### Post by aysiu on 2006-11-10
There's no need to install *ubuntu-desktop* if you want KDE. Try this instead: ```
sudo aptitude update && sudo aptitude install kubuntu-desktop x-window-system-core kdm
sudo /etc/init.d/kdm restart
``` You may not need to explicitly say *x-window-system-core* and *kdm*, but I threw those in just to be safe (since you said you cannot get into the xwindow).

---

### Post by GTonizuka on 2006-11-10
thanks for the reply,
i will try that as soon as i get home.
hopefully i will write my next message from my recovered kde...
^^

---

### Post by GTonizuka on 2006-11-11
well ok, the result was quite different than i expected, but i managed to get my old KDE desktop by playing around with ubuntu-desktop, kubuntu-desktop, kdm and gdm...
anyway thanks a lot for the reply : )

---

