---
title: "Ubuntu can't find netflix-desktop package."
date: 2016-06-09
forum: General Help
---

### Post by arthur24 on 2016-06-09
sudo apt-add-repository ppa:ehoover/compolio
sudo apt-get update
sudo apt-add-repository ppa:pipelight/stable
sudo apt-get update
sudo apt-get install pipelight-multi

I even enabled pipelight manually as instructed on a website with >>

sudo pipelight-plugin --enable silverlight

Followed by >>

sudo apt-get install netflix-desktop

Which gives the error | ```
E: Unable to locate package netflix-desktop
```

In software & updates I checked the allowance of Canonical, community, proprietary driver and sofware restricted software and checkboxed all the PPAs in the "other software" tab of Software & updates window.
I even rebooted the computer (more a ritual then a neccesity) and then tried to install netflix again giving the same error.

Oh, and I use Ubuntu 16.04 xenial.

---

### Post by X-RED_Tech on 2016-06-09
You're probably using an outdated guide...
And why go to so much trouble with unofficial clients ("hacks") running emulated with Wine, etc. when you can just install **Google Chrome**?

---

### Post by arthur24 on 2016-06-09
You're probably right about using a outdated guide. And I am using it with Google Chrome.
But I had the Desktop app running on 14.04 and I found it rather usefull and worked flawlessly. Just óne click on the app and launch.
So it's my personal preference to see it work through the application which is the reason for opening this thread.

So if there is a up to date procedure for getting the Netflix app to work I would like to hear about it.

I'm not sure what you mean by "hacks" ?? 
Me among many may want to run applications intended for Windows and are therefore forced to use Wine. I use Wine for many purposes and is actually required to run several apps I use.
Is Wine a hack? I heard it has leaks, but it's no reason for me not to use it since I need it. I'm still going to use it for the few Windows apps and games I use so it's here to stay.

I hope theres a up to date procedure, please let me know.

---

### Post by X-RED_Tech on 2016-06-09
If you use Wine in order to use several Windows software why don't you just use Windows? Much simpler... Any emulated software is an "hack" by definition but nothing bad in itself because of that, it's just your prejudice acting upon. Now, I'm sure you think you need all that Windows only software but most likely you don't. If you're adamant about such software then, again, using the native OS for such software is the best option. 

[http://www.howtogeek.com/130372/how-to-watch-netflix-on-ubuntu-with-the-netflix-desktop-app/](http://www.howtogeek.com/130372/how-to-watch-netflix-on-ubuntu-with-the-netflix-desktop-app/) <- This should still work in 16.04 because the PPA supports it.

---

### Post by arthur24 on 2016-06-09
That is the same guide I used, it doesn't work. The same terminal commands according to that guide are the ones I already used and you will see that mentioned in the OP. Everything is fine with Wine btw.

As for my prejudice you seem to detect. My only one is that I do not like Windows, I don't have any copies lying around, and I'm not going to spend the bulky amounts of money on it which Windows isn't even worth. Especially since I would only need it for a few apps and games. The amount of Wine apps here are scarce. Most of my installed software is build for Linux. I'd rather install a hack then pay for Windows.
And while your absolutely correct about the things you say, I post on the Ubuntu forums, not somewhere else like a Windows oriented site.
So why I get Windows advice escapes me.
You may have your own opinions or preconceptions, which is fine because your a free man, but it is rather ironic since you mentioned the word prejudice.
The topic title and the thread contents are very clear though, I kinda hoped the same could be said about the answers even although I appreciate your attention.
The problem is still bothering me so if anybody knows the solution I would really appreciate it.

---

### Post by SeijiSensei on 2016-06-09
Netflix-desktop is distributed nowadays as part of Pipelight. [Add the Pipelight stable PPA]("https://launchpad.net/~pipelight/+archive/ubuntu/stable") and see if you can install netflix-desktop:
```

sudo add-apt-repository ppa:pipelight/stable
sudo apt-get update
sudo apt-get install netflix-desktop

```

---

### Post by X-RED_Tech on 2016-06-09
There... Lucky you, you got yourself an expert. :)
Please try the method outlined in the post above.

I have nothing to add, technical or otherwise. But I would like to comment about the misunderstanding. I meant to say you seem to have a prejudice against the "hack" concept and you shouldn't. Hacking is our bread&butter.
This post explains it a lot better and coincidentally is in a thread about Netflix: [http://ubuntuforums.org/showthread.php?t=2327274&p=13501811#post13501811](http://ubuntuforums.org/showthread.php?t=2327274&p=13501811#post13501811)

---

### Post by arthur24 on 2016-06-10
@SeijiSensei

Unfortunately that also doesn't work. And to be honest, I already tried installing the pipelight ppa and apt-get updated everything.
Not that you would or should specifically try it just for my troubleshooting, nor that you should litter your computer with let's say the Netflix App which you may not care about, but can you get it installed through that procedure on 16.04?
If Yes then I am missing something entirely besides the Pipelight and/or ehoover ppa that I'm unaware off. Ubuntu itself is fully updated. As for Wine, it works flawlessly and can easily navigate to winecfg.

@X-RED_Tech.

Always unpleasant to have misunderstandings. I'm sure I gave you the impression about being prejudice against hack concepts somehow. I can't tell how though, because I don't. 
I do use Google Chrome for Netflix for the time being, and if there is no solution to get the app to work then I have no choice but to stay with Google chrome. Getting the app to work is more a luxury for me then a necessity. But I want to see it work if possible.
I did read everything google could throw at me. These are outdated guides by definition as I seem to be the first to try the Netflix app on 16.04 and opens a thread about it not finding the package. I have already tried your suggestion, and also the pipelight ppa that Sensei suggested.
I'm not going to make assumptions. All I'm saying is that I always succeeded installing the Netflix app on 14.04 with above procedures but it simply seems to be not compatible, or something else is missing on my machine. If it's the former then I hang, but if it's the latter then what else could I try?

---

### Post by SeijiSensei on 2016-06-13
Looks like netflix-desktop has been removed from 16.04, which isn't surprising since development stopped on that package a couple years back in favor of pipelight.  On the [PPA page for Pipelight]("https://launchpad.net/~pipelight/+archive/ubuntu/stable"), the last version of netflix-desktop is for 15.10, and if you filter for Xenial you won't see netflix-desktop on the list.

---

