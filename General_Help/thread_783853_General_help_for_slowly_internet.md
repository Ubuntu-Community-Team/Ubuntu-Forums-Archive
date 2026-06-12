---
title: "General help for slowly internet"
date: 2008-05-06
forum: General Help
---

### Post by LitusMayol on 2008-05-06
Hi everyone!

I'd like to request some general help for Internet. I'm having some speed problems with the Internet. It is running so slowly and it turns to grey tonality so often with simple actions like opening a new flap, or writting a new direction... And the problem is that I don't really now why it happens... 

If anybody could help me.

Thanks, and pardon the newbie! ;)

---

### Post by danwood76 on 2008-05-06
May be able to help, a few questions first.

Are you running any bit torrent clients?
What internet connection speed do you have?
What browser are you using?

---

### Post by shifty_powers on 2008-05-06
the turning grey sounds like a problem with the browser itself rather than the speed of the internet.

Have you tried doing a speedtest on the internet or using another browser?

(I'm assuming you've got compiz running by the sounds of it, one of the plugins turns a windows grey when it is busy for any period of time...)

---

### Post by LitusMayol on 2008-05-06
> May be able to help, a few questions first.

Are you running any bit torrent clients?
What internet connection speed do you have?
What browser are you using?

 Yes I'm running aMule but never had these problems before. They just appeared. I'm using a normal ADSL 3Mb connection. I'm using Firefox.

	
> the turning grey sounds like a problem with the browser itself rather than the speed of the internet.

Have you tried doing a speedtest on the internet or using another browser?

(I'm assuming you've got compiz running by the sounds of it, one of the plugins turns a windows grey when it is busy for any period of time...)

Oh man, you're surprising me! Yes I've Compiz running! I've never done a "*speedtest*" and I don't now how to do it...


Thanks anyway for both!

---

### Post by shifty_powers on 2008-05-06
ok try using something like opera, or if you are using ubuntu 8.04, that means you are probably using firefox 3 beta. Now, it's worked fine for me, but you might want to try fifrefox 2, which is a more stable product than ff3, which is a beta after all.

don't know where you live, but i often use [http://www.speedtest.net/](http://www.speedtest.net/) - this will enable you to gauge wether your internet is slow or if it is just a software prob.

I would run it first with amule running, and then without, and go from there ;)

---

### Post by LitusMayol on 2008-05-06
Hei!

Here comes the speedtest result:

[[IMG]http://www.speedtest.net/result/267960243.png[/IMG]](http://www.speedtest.net)

I think it's fine, no? But I not really sure, 'cause i've nevere seen one so... What d'you think?


Konqueror and Opera work fine, not perfect but rather better than Firefox. Maybe it's the FF3 Beta the problem, but 'till now it has run really good. 


Thanks again!

---

### Post by shifty_powers on 2008-05-06
well that is perfectly respectable for a 3mbit connection.

not as good as mine but nevermind ;) hehe

[[IMG]http://www.speedtest.net/result/243337955.png[/IMG]](http://www.speedtest.net)

but anyway, try this.

```
sudo apt-get remove firefox
```

followed by

```
sudo apt-get install firefox-2
```

oh and 

```
sudo apt-get autoremove
```

is also handy from removing redundant packages.

Course you could just go into synaptic as well ;)

edit: and if you ever want to go back to ff3 then reverse it:

```
sudo apt-get remove firefox-2

sudo apt-get install firefox
```

should get you back to ff3beta5, the default firefox package in the hardy repos is ff3, (which is why you have to specify firefox-2 to apt).

---

### Post by LitusMayol on 2008-05-06
Hi again! 

FF2 is working really good. FF3 stills having some problems. By the way I'll use the 2, and in some week I'll use the 3 (in order to prove if it have improved). If in a pair of weeks FF3 works without problems I'll work with it again, instead of using the "*old*" one.

Thanks everyone indeed!

(It is solved, can anyone mark the thread as solved, i thought it was on thread tools but it isn't there. Thansk again.)

---

