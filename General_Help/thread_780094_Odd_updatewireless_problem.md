---
title: "Odd update/wireless problem"
date: 2008-05-03
forum: General Help
---

### Post by sharpeg on 2008-05-03
This is an odd one.

I seem to have sorted out my Hardy Hangs and now have an 'almost' stable system. My one outstanding problem is an odd one. 

I am in the process of updating Rhythmbox to use my music library from a NAS. I'm using a wireless connection. Every now and again, I get prompted to look for a codec. When I click though to get the codec, it hangs (before asking for the password). and I have to reboot to get rid of the window.

Now that's a problem in itself, but the odd bit is that if I connect to the network with a wire, it doesn't seem to have a problem. The same probelm occurs if I try to use package manager or update manager to get extra software wirelessly. Again, the problem doesn't seem to occur if I use a wired connection.

Any ideas?

---

### Post by strabes on 2008-05-03
You should probably just install all the codecs to begin with. It's easier than installing them one by one as you try to play different media files. Before running the following command you should enable the [Medibuntu repository](https://help.ubuntu.com/community/Medibuntu) as it has packages which will allow you to play DVDs, etc.

sudo aptitude install -y w32codecs ubuntu-restricted-extras libdvdcss2 libxine1-bin libxine1-ffmpeg ffmpeg

---

### Post by sharpeg on 2008-05-03
Thanks for that. Makes perfect sense. However...

I don't know if this is a new problem or something I'm doing wrong.

I started terminal and entered the commands you pointed me to and terminal said

geoff@geoff-laptop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
sudo: unable to resolve host geoff-laptop
geoff@geoff-laptop:~$ 

Am I doing something wrong or have I found another problem?

Update: Fixed this one all by myself! In the process of getting my network shares working I had managed to add a domain name to my computer. Used Network to remove this and hey presto, termonal was happy with the commands!

Thanks

---

