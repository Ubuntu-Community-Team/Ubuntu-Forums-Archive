---
title: "What is needed to install the updated gparted 0.3.3.?"
date: 2007-05-06
forum: General Help
---

### Post by dryder on 2007-05-06
Hi,

I am starting this thread anew as my last got hijacked and confusing (not complaining - stating the reason for what might appear double posting).

After installing gparted via synapting and then uninstalling it, I had installed gpatred 0.3.3 from [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) successfully but for reasons of my own doing I had to reinstall ubuntu.

Now I am trying to install gparted 0.3.3 again 'clean'.

But I am having a lot of problems finding out what packages I need to install first in order to get goarted 0.3.3 to install via terminal.

I have tried to install gtkmm 2.10.x  from gtkmm but it doesn't want to install.

Can anybody who has successfully installed gparted 0.3.3 tell me the list of packages they needed to install it please?

Many thanks,
David :-)

---

### Post by rsambuca on 2007-05-06
I haven't installed gparted 0.3.3, but I had a look at the requirements for you.  It appears that the two packages you have to install first are:

Parted 1.7.1 or greater, and gtkmm 2.8 or greater (called libgtkmm-2.4-1c2a).

Both of those are already available in the ubuntu packages, so you can just install them via the command line, or perhaps the easier way would be to install them via synaptic package manager.

It says the ubuntu gtkmm is 2.4, but according to the website, most distros actually use a higher version, so I assume it should work fine.

I'll assume you don't want to just use gparted as the liveCD for some reason, eventhough it is usually easier to use since no drives are mounted.

---

### Post by dryder on 2007-05-06
Thanks rsambuca - and I appreciate the fast reply.

I will install these from synaptic - I had tried to install the downloaded packages as they were more recent (it appeared) versions - thanks.

No, at this stage I don't want to use LiveCD.

But I have an additional Q: when installing Ubuntu one can label the partitions with real names ( I have one I call 'graphics').

But when using the label function of gparted it says that labelling will "destroy all data on sda!" These partitions I want to set up are on a Windows drive - is this message saying it will delete all the Windows partition??? This message needs clarifying in the wiki - or better phrased in gparted ..

Many thanks
David

---

### Post by dryder on 2007-05-06
Still no luck on gparted-0.3.3 - ./configure went OK but make gave this:

david@ubuntu-server:~/Desktop/gparted-0.3.3$ make
make  all-recursive
make[1]: Entering directory `/home/david/Desktop/gparted-0.3.3'
Making all in compose
make[2]: Entering directory `/home/david/Desktop/gparted-0.3.3/compose'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/david/Desktop/gparted-0.3.3/compose'
Making all in include
make[2]: Entering directory `/home/david/Desktop/gparted-0.3.3/include'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/david/Desktop/gparted-0.3.3/include'
Making all in pixmaps
make[2]: Entering directory `/home/david/Desktop/gparted-0.3.3/pixmaps'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/david/Desktop/gparted-0.3.3/pixmaps'
Making all in po
make[2]: Entering directory `/home/david/Desktop/gparted-0.3.3/po'
file=`echo ar | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file ar.po
/bin/sh: -o: not found
make[2]: *** [ar.gmo] Error 127
make[2]: Leaving directory `/home/david/Desktop/gparted-0.3.3/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/david/Desktop/gparted-0.3.3'
make: *** [all] Error 2
david@ubuntu-server:~/Desktop/gparted-0.3.3$ 

Any clues please?

Thanks
David

---

### Post by rsambuca on 2007-05-06
Sorry, I have no idea how to help you with these errors.  Perhaps you might consider the rpm and converting it to a deb package using alien.  the rpm's for the latest gparted can be found [[COLOR="Red"]here[/COLOR]]("http://rpmseek.com/rpm-pl/gparted.html?hl=com&cs=gparted:PN:0:0:0:0").

---

### Post by dryder on 2007-05-07
rsambuca,
> Sorry, I have no idea how to help you with these errors.

Solved it thanks ... :-)

---

### Post by rsambuca on 2007-05-07
Well, share!  How did you fix the error?  It might help others in the future.

---

### Post by dryder on 2007-05-07
> Well, share! How did you fix the error? It might help others in the future.

True - but all I did was remove the 'latest version', 'needed' packages installed from the relevant sites and install those in the ubuntu repositories.

Just goes to show it is worth trying the versions in the repositories before downloading versions that are 'must be this version or higher' ... 

Hope that makes sense !

David

---

