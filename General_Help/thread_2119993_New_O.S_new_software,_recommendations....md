---
title: "New O.S new software, recommendations..."
date: 2013-02-25
forum: General Help
---

### Post by Tuexnovia on 2013-02-25
Hi guys I'm gonna give a try to my new O.S.


What about my drivers where can I find them? Aspire one D257 13dqrr Atom N455

Codecs for Gnome player.

Something to read NTFS (I got C and D in the same HDD and in C I got win and lub and in D dates)
Is there any kind of firefox to be able to use autocorrect.

Really thanks guys...

---

### Post by Tuexnovia on 2013-02-25
Wow I've tried to download adobe flash and I got a folder and there is not any .exe jajaja I know I'm kidding but how can I install it?

Wow so many new things... Rpm .gz and yum o god help...

Later I'm gonna follow a guide about how to use it, but if you by the time can help me.


Thanks....

---

### Post by carl4926 on 2013-02-25
Open a terminal

```
sudo apt-get update && upgrade
```

Later you might want also
```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

Re: [http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)

---

### Post by timgood on 2013-02-25
Firstly, welcome to Ubuntu.

As far as drivers are concerned, what is not working that is supposed to work? Graphics drivers can be installed from the Ubuntu Software Centre.

You should not have to download or install .rpm files, as Ubuntu is based on Debian and uses the .deb format. You should be able to find just about everything you need in the Ubuntu Software Centre, from where you can install with just one click. If you have specific requirements for other software, let us know and we will try to help.

---

### Post by Tuexnovia on 2013-02-25
> **carl4926 said:**
> Open a terminal

```
sudo apt-get update && upgrade
```

Later you might want also
```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

Re: [http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)


ok really thanks guys I finally got it, now I'm trying to install Skype is like a joke I don't even know what I'm doing xDD

I use pidgin and I downloaded from synaptic package the extension or package (I'm new sorry) "pidgin-skype" and now appears skype in pidgin but I can just put my name that's all.


I'm really happy with Lubuntu really fast but I have to check tutorials and so on, because I'm completely lost.

---

