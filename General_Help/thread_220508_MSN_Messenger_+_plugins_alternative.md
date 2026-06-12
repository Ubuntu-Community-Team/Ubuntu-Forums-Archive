---
title: "MSN Messenger + plugins alternative?"
date: 2006-07-21
forum: General Help
---

### Post by Donnieboii on 2006-07-21
Hello.. ive been on ubuntu for 2 weeks now and exploring and reinsalling and try to understand alot... yesterday I did my final install and ry to get all plugins and stuff working wich all went ok... but now today i tried wine for msn caus i dont like gaim and amsn cause they dont do the msn plus wich a like because everyone uses color in their name and i cant read their name propley in gaim so my question is.. how do i get MSN 7.5 + plus working in wine? or is there any other way of getting msn plus plugin to work?

all help is appriciated and when i get a little better i'll be there for the newB's to.

Thanks..

p.s. my english isnt optimal so sorry for mistakes

---

### Post by el_rata on 2006-08-06
for amsn there is a plus plugin ... its very easy to install .... [http://amsn.sourceforge.net/plugins.php](http://amsn.sourceforge.net/plugins.php) ... install it in the folder .amsn/plugins ... i think thats all.

---

### Post by ironfistchamp on 2006-08-07
I tried to get MSN7.5 working in wine but no cigar. The furthest I got was the login screen. To get the correct installer you need one that was changed for win2000. I think there is one on [www.mess.be](www.mess.be)

I couldn't get past the login screen. It wouldn't accept my details.

---

### Post by patrickfromspain on 2006-08-07
you can install amsn 0.96rc1 and some plugins. All is in amsn.sourceforge.net

---

### Post by DAFORZE on 2006-08-07
hmm i find amsn a little bit ugly and stuff. It would be a lot better to get msn messenger 7.5 to work via wine!
I wonder if somebody has got this to work?

---

### Post by patrickfromspain on 2006-08-07
Amsn ugly? Not mine, my friend ;)

A quick guide on how to solve ;)

go to [http://200.126.104.121:8080/Ubuntu/breezy/tcl-tk/](http://200.126.104.121:8080/Ubuntu/breezy/tcl-tk/) and download tcl8.5, tcl8.5-dev, tk8.5 and tk8.5-dev debs. Install all of them. Then, in amsn.sourceforge.net download the source code. Unpack it, and in a Terminal cd to the unpacked folder, ./configure and check that at the end you get tk and tcl 8.5. make, make install and you have a nice amsn. 

But tcl/tk8.5 has a bug. So, you will need to install the desktop integration plugin in order to browse files (to send, or to change your display picture). If you install the plus plugin you'll get some nice features.

---

### Post by patrickfromspain on 2006-08-07
you can also check that:
[http://www.ubuntuforums.org/showthread.php?t=216689&highlight=amsn+0.95](http://www.ubuntuforums.org/showthread.php?t=216689&highlight=amsn+0.95)

---

### Post by ironfistchamp on 2006-08-07
I have 0.96RC1 and it looks great. I like it more than the real thing although it is a little slow sometimes.

---

### Post by DAFORZE on 2006-08-12
I now use amsn 0.97b.
I still want to use msn messenger 7.5, because amsn is not fully compatible with msn 7.5. I know maybe it sounds exagerrated(sp?) but i would really like to have 100% functionality of all msn features. In Holland really everybody has an msn account and use the msn 7.5 client. So sometimes its annoying when so many people can't send me a voice message because amsn doesnt have that function implemented yet. When this happens, it feels sometimes that like their are on a superior OS. :mad:

---

### Post by ironfistchamp on 2006-08-12
100% compatibility isn't going to be easy because MSN Messenger (now Windows Live messenger which sucks) is closed source. The programmers have to figure their own way around a certain problem rather than being able to browse MSNs source code and see how they did it. I think that they have done an amazing job and it is getting better all the time. 

As for the superior OS. All you need is a week limited to XP and you will realise how wrong you are :p well thats what I think anyway. The Live CD won't work on this here computer. Doesn't like the whatever graphics it has.

I hope aMSN becomes more to your liking in the future or you find a way to run the real thing. If you do find a way post back asap I am sure many people will be happy to try it.

Ironfistchamp

---

