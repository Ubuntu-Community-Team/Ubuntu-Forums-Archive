---
title: "Problem installing digikam from Terminal"
date: 2014-05-25
forum: General Help
---

### Post by claes2 on 2014-05-25
I'm trying to install digikam and ran into some difficulties.  I tried using the following commands to install from Terminal:

$ sudo add-apt-repository ppa:kubuntu-ppa/backports
$ sudo apt-get update
$ sudo apt-get install digikam

And got to the last one:

$ sudo apt-get install digikam 

When I received this message:

user@chrubuntu:~$ sudo apt-get install digikam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 digikam : Depends: libkface2 (>= 1.0~digikam3.5.0) but it is not going to be installed
           Recommends: ffmpegthumbs but it is not going to be installed or
                       mplayerthumbs but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
user@chrubuntu:~$

Can someone help walk me through a fix for this if it looks familiar?

---

### Post by SeijiSensei on 2014-05-25
Is there a reason you're using the backports PPA?  That's probably the reason why you have unresolved dependencies.  I've always just installed digikam normally without a PPA, but then I use Kubuntu to begin with.

---

### Post by claes2 on 2014-05-25
> **SeijiSensei said:**
> Is there a reason you're using the backports PPA?  That's probably the reason why you have unresolved dependencies.  I've always just installed digikam normally without a PPA, but then I use Kubuntu to begin with.
Actually I was having trouble installing it any other way heh, still am.  The reason that I want to install digikam is because I am unhappy with Shotwell and want to replace it.

Also, I was able to install PhotoQt with the following commands:

sudo add-apt-repository ppa:samrog131/ppa
 sudo apt-get update
 sudo apt-get install photoqt

But I would like to uninstall it and I am not sure how.  I am looking for a good, lightweight photo manager for Ubuntu 14.04 and so two things remain that I would like to do:

1) I want to install digikam in a way that would be easy for me to uninstall if I don't care for it, like I did with Shotwell.  I couldn't find a deb package for it.

and

2) And I would like to uninstall PhotoQt however I can.  I already removed the PPA's with this command:

sudo add-apt-repository -r ppa:samrog131/ppa

And am looking for some guidance to get me through the rest of the uninstall on that application or some help with understanding what I am doing wrong.

Thanks in advance!

---

### Post by monkeybrain20122 on 2014-05-26
> **claes2 said:**
> 
  I already removed the PPA's with this command:..


That seems to be the source of your problem. Removing a ppa is really simple, you could have just unchecked it in synaptic without any command, but the packages you have installed from there don't get removed, so say you have installed A version 2 from ppa, now you want to install B, it would require C version 1 normally, but if C also depends on A it would require version 2 to match. Now the ppa would normally provide also C version 2, but you have removed it without downgrading A so you are stuck.

The proper way to downgrade packages installed from ppas is by ppa-purge. First you need to install it
```
sudo apt-get install ppa-purge
```
Then you need to reactivate the ppa you need to purge. In this case you would have to re-add the repository and run sudo apt-get update
Then run
```
sudo ppa-purge ppa:samrog131/ppa 
```

---

### Post by claes2 on 2014-05-26
If I re-add the ppa package, run apt-get update again, and then run ppa-purge on the ppa will it uninstall PhotoQt as well?  Sorry I'm still a little unclear on that.  Thank you for your response though!  Each thread I learn a little more ;)

---

### Post by claes2 on 2014-05-26
> **monkeybrain20122 said:**
> That seems to be the source of your problem. Removing a ppa is really simple, you could have just unchecked it in synaptic without any command, but the packages you have installed from there don't get removed, so say you have installed A version 2 from ppa, now you want to install B, it would require C version 1 normally, but if C also depends on A it would require version 2 to match. Now the ppa would normally provide also C version 2, but you have removed it without downgrading A so you are stuck.

The proper way to downgrade packages installed from ppas is by ppa-purge. First you need to install it
```
sudo apt-get install ppa-purge
```
Then you need to reactivate the ppa you need to purge. In this case you would have to re-add the repository and run sudo apt-get update
Then run
```
sudo ppa-purge ppa:samrog131/ppa 
```
 I followed these instructions and successfully purged the PPA, and then successfully removed PhotoQt with the Software Center.  I assume this means that I have removed it completely.

Now, back to the question in the title of the thread:  how do I best install digikam in Ubuntu 14.04?

---

### Post by RedRat on 2014-05-26
Why not just install it through Synaptic? It is there. That is how I installed it in 14.04. But be forewarned that digikam does have some bugs that are being worked on, it ain't perfect yet. For some things it does OK but for some things, like ridding a folder of duplicate pictures it seems to have problems--this goes back to earlier versions. Also be aware that I think digikam is a KDE program so it downloads KDE components to your computer--nothing really wrong with that.

---

### Post by claes2 on 2014-05-26
> **RedRat said:**
> Why not just install it through Synaptic? It is there. That is how I installed it in 14.04. But be forewarned that digikam does have some bugs that are being worked on, it ain't perfect yet. For some things it does OK but for some things, like ridding a folder of duplicate pictures it seems to have problems--this goes back to earlier versions. Also be aware that I think digikam is a KDE program so it downloads KDE components to your computer--nothing really wrong with that.

Ahhh and that is why it uses packages from the kubuntu ppa?  Ok, I am actually thinking twice about digikam now and most likely going back to Shotwell.  The entire reason that I was trying other photo managers was because I was trying to get applications that were smaller and more functional but I just installed Ubuntu Tweak today and cleared about 1.3GB of space from unneeded and/or cached packages and old kernels and whatnot and my system is purring again.  There's nothing really wrong with Shotwell I just wanted something smaller but now that I am learning more and more I am finding that my problem was more all of the old and left behind packages from all of the applications that I have been installing and things are running great again.

Marking thread Solved.  Thanks for everyones input I'm learning so much so quickly ;)

---

### Post by RedRat on 2014-06-13
I have tried Shotwell but find it very limiting. I guess if you don' t have a lot of photos it may work for you. It is too bad that they can't get the bugs worked out in DigiKam since I think it is light years ahead of programs like Shotwell. But I can see why Digikam has its problems. It is powerful (at least potentially) and has a lot of stuff in it, so it is going to take a dedicated group to debug it and get it working the way they like.

---

