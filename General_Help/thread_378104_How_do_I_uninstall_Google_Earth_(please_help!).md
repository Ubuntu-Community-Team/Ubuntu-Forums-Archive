---
title: "How do I uninstall Google Earth (please help!)"
date: 2007-03-06
forum: General Help
---

### Post by Tahir on 2007-03-06
I am new to the whole ubuntu thing and I am wondering how I would go about **un**installing Google Earth.  Although I can find **installation**  in the community documentation,  I cant find anything about **uninstallation** guide too.

I know that there is a rpm to deb converter but is there a bin to deb converter because I want to install this cleanly. 

I know that to uninstall, all you would have to do is sudo apt-get remove googleearth.

Please help me.  You can point me to another thread if it answers my questions fully.

Anyway, I want to install it in the proper way. I am not going to add more repos because I want to learn how to do this rather than taking the easy way out.  Also I would not take the automatic way because that is even worse for me because then it would prove to me that I have learned nothing.  

Please help me out here.

-Tahir

---

### Post by taurus on 2007-03-06
How did you install GoogleEarth in the first place?  With it, you just have to remove the directory where you installed it and remove the link to the binary in that directory.  Then, you just change the permission of the GoogleEarthLinux.bin and execute it to install it.

```
chmod 755 GoogleEarthLinux.bin
./GoogleEarthLinux.bin
```

---

### Post by ramjet_1953 on 2007-03-07
Tahir, I suspect that the techno-speak that Taurus came back to you with probably went right over your head?

Some people are really good as scaring-off newcomers.

I suggest that Automatix2 may be the answer you are looking for.
It will automatically download and set-up Google Earth for you, and lots of other things, including the audio and video codecs, if you choose to do so.

After you have been around Linux for a while, you will get used to using the command line and the incredible power and flexibilty that it offers. However, lets just get things going for you first.

[http://www.getautomatiix.com](http://www.getautomatiix.com)

Regards,
Roger 8)

---

### Post by jocko on 2007-03-07
@Taurus & ramjet_1953: Hey guys, he actually asked how to **uninstall** it.

@Tahir: If you installed it using GoogleEarthLinux.bin you downloaded from google, this is how to uninstall it (run these commands in a terminal):

```
cd ~/google-earth
sh uninstall
```

---

### Post by ramjet_1953 on 2007-03-07
Jocko, If you read down a little further, you will see that he wants to re-install it.

Regards,
Roger :cool:

---

### Post by Mr LG on 2007-03-07
You could also try 

Sudo apt-get remove google\ earth

I have had google earth and had to remove it. I'm pretty sure that worked for me.
You might have play around with the wording.. maybe Google\ Earth or googleearth.

---

### Post by jocko on 2007-03-07
> **ramjet_1953 said:**
> Jocko, If you read down a little further, you will see that he wants to re-install it.

Regards,
Roger :cool:

sorry, I didn't read properly...

---

### Post by Tahir on 2007-03-07
Thanks all for the replies guys. 

Just for the record, I had not installed it, but I was worried that if I do then how would I go about uninstalling it.  

[QUOTE="jocko"]sorry, I didn't read properly...[/QUOTE]

You actually did. The thing is anyone can read the instructions and then install it, but how to uninstall it?  That is why I posed the the question.  Also I dont like the idea of just deleting the folder that something was installed in.  Are there not loads of links that need to be deleted too? 

[QUOTE="Mr LG"]You could also try

Sudo apt-get remove google\ earth

I have had google earth and had to remove it. I'm pretty sure that worked for me.
You might have play around with the wording.. maybe Google\ Earth or googleearth.[/QUOTE]

But you cant do this if you did not install something in the "official" using apt-get, aptitude or synaptic etc. I was executing a .bin file not a .deb package.

[QUOTE="ramjet_1953"]
Tahir, I suspect that the techno-speak that Taurus came back to you with probably went right over your head?[/QUOTE]

No it actually did not.  I understood everything he said but I was talking about UNinstallation and he was talking about INstallation which in in the community documentation anyway. 

[QUOTE="ramjet_1953"]
I suggest that Automatix2 may be the answer you are looking for.
It will automatically download and set-up Google Earth for you, and lots of other things, including the audio and video codecs, if you choose to do so.[/QUOTE]

Allegedly, Automatix messes up people's config files.   I also want to learn the basics of the linux command line. Imagine if I wanted to install a different program that I cant get thru adding a repo or using Automatix then how would I go about installing it?

That is the reason.  Also I would like to edit the ubuntu entry on the subject:

[https://help.ubuntu.com/community/GoogleEarth?highlight=%28earth%29%7C%28google%29](https://help.ubuntu.com/community/GoogleEarth?highlight=%28earth%29%7C%28google%29)

and talk about how to uninstall.  But is there a page on that in the community documentation explaining how to uninstall anything that was installed thru a .bin file?

Moving on, do bin installation files always leave behind an uninstall file?  Are there names other than "uninstall" that they take?  I would like to know this because I want to get rid of realplayer.  Perhaps then install it a more convenient location like /opt.

Thanks again for all your replies,
-Tahir

---

### Post by camellochapin on 2007-04-09
> **jocko said:**
> @Taurus & ramjet_1953: Hey guys, he actually asked how to **uninstall** it.

@Tahir: If you installed it using GoogleEarthLinux.bin you downloaded from google, this is how to uninstall it (run these commands in a terminal):

```
cd ~/google-earth
sh uninstall
```

Thanks a lot!  I just wanted to uninstall Google Earth from my laptop and your post worked perfectly!

---

### Post by fakie_flip on 2007-05-17
If you installed Google Earth as root, try this.
```

sudo su -
cd /opt/google-earth/
export DISPLAY=:0
./uninstall
```

---

### Post by Angelbeast on 2007-05-19
i'm doing a fresh install of google earth and it wants to install it in my home directory...i wntto install it in the regular app directory...what would that be?

---

### Post by taurus on 2007-05-19
You mean you want to install it outside your $HOME directory.  In that case, you need to run it as root since you need to have the write permission to write to it.

```
sudo ./GoogleEarthLinux.bin
```
Then, specify the directory you want to install it.

---

### Post by Angelbeast on 2007-05-19
> **taurus said:**
> You mean you want to install it outside your $HOME directory.  In that case, you need to run it as root since you need to have the write permission to write to it.

```
sudo ./GoogleEarthLinux.bin
```
Then, specify the directory you want to install it.

well i actually went ahead and installed it in the default directory. But i'm having this problem:
[http://ubuntuforums.org/showthread.php?t=448902](http://ubuntuforums.org/showthread.php?t=448902)

---

### Post by pollux_master on 2007-06-05
> **fakie_flip said:**
> If you installed Google Earth as root, try this.
```

sudo su -
cd /opt/google-earth/
export DISPLAY=:0
./uninstall
```

Thx ***fakie_flip***,

Worked fine for me!

---

### Post by cronqvist on 2007-10-29
> **fakie_flip said:**
> If you installed Google Earth as root, try this.
```

sudo su -
cd /opt/google-earth/
export DISPLAY=:0
./uninstall
```

Whereas other methods didn't work for me, this one actually got the job done. Thank you very much! :)

---

### Post by boxfullofheads on 2008-04-17
Hi,
I just wanted to say thank you for this info, i am new to linux
3 days now and i installed Google Earth with GoogleEarthLinux.bin
and it would not respond when i ran it and i did not know how to
uninstall it so i looked and found this info.. i was able to uninstall
it from root. thanks again

---

### Post by Inrisalvation on 2008-04-28
Fakie_flip

Thank you. The code you provided worked perfectly.

---

### Post by DrDeo on 2008-05-06
@fakie_flip 

thats the only thing that worked for me too. 

thankyou.:KS

---

### Post by antlachance on 2008-06-16
> **fakie_flip said:**
> If you installed Google Earth as root, try this.
```

sudo su -
cd /opt/google-earth/
export DISPLAY=:0
./uninstall
```

This one worked perfectly for me.  Thanks.

---

