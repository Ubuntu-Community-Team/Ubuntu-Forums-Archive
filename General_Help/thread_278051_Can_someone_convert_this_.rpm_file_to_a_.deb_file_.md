---
title: "Can someone convert this .rpm file to a .deb file for me?"
date: 2006-10-15
forum: General Help
---

### Post by DiscoSamurai on 2006-10-15
I know I can use alien but I have no clue on how to install that, slack ware, as well as java. It's be much easier if someone could convert [limewire.rpm]("http://www.limewire.com/LimeWireSoftLinux") for me into a .deb file.

---

### Post by treris on 2006-10-15
Check out frostwire

it is basically an adware free version of limewire and there are ubuntu/debian packages 

[site]("http://www.frostwire.com/")

direct download [here]("http://www.frostwire.com/download.php?file=http://www.peercommons.com/frostwire/4.10.9/FrostWire-4.10.9-2.i586.deb")

hope that helps,

you'll still need java though

---

### Post by DiscoSamurai on 2006-10-15
Okay, I'll do that, but first, in great detail, explain to me how to get java?

---

### Post by blackmh on 2006-10-15
[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by taurus on 2006-10-15
> **DiscoSamurai said:**
> Okay, I'll do that, but first, in great detail, explain to me how to get java?

Download and install Automatix first.  Then fire up Automatix and install java, frostwire, or whatever else you want with it...

[http://getautomatix.com/](http://getautomatix.com/)

---

### Post by slibuntu on 2006-10-16
I've got a kinda howto on installing limewire, including converting the rpm file on my blog, dunno if it'll work but its worth a try! Link below, and its in the essential apps section

---

### Post by dannyboy79 on 2006-10-16
you could convert it yourself if you want to, simply first do sudo aptitude install alien. then use alien to change the rpm into a deb then install the deb. you'll have to gogle how to use alien, i used it once but I forgot how.

---

### Post by taurus on 2006-10-16
> **dannyboy79 said:**
> you could convert it yourself if you want to, simply first do sudo aptitude install alien. then use alien to change the rpm into a deb then install the deb. you'll have to gogle how to use alien, i used it once but I forgot how.

```
alien filename.rpm
sudo dpkg -i filename.deb

```

---

### Post by _duncan_ on 2006-10-16
Instead of using the rpm package, you're better off downloading the zip package from the limewire website.

As long as you have java working, all you have to do is unpack the zip file into a folder inside your home directory, then use java to run the jar file.

You still need java anyway even if you install limewire using the rpm package, so focus first on getting java to work. Same thing goes for frostwire. The root problem here is java.

---

### Post by Old Pink on 2006-10-16
I've converted it, PM me with an email address I can send it too. :)

---

