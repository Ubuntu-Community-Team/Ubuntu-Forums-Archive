---
title: "strategic conquest game wont load html"
date: 2015-12-02
forum: General Help
---

### Post by kccv42 on 2015-12-02
I have this game originially made for mac but a developer put it on the web. I am unable to load this using my ubuntu computer. I looked at the FAQ and it said something about the javascript console needed to be enabled in chrome. Here is the link of the game. [http://mmcnicol.github.io/StratConClone/play/](http://mmcnicol.github.io/StratConClone/play/)

---

### Post by QDR06VV9 on 2015-12-02
Do you have java blocker on?
Works good on Chromium but I did have to enable Java and Disable UBlock Origin for that site to work.
Regards

---

### Post by kccv42 on 2015-12-02
I dont think i have that java blocker on but i am not sure. How can i check?  How do you enable java on chromium and disable UBlock Origin?

---

### Post by QDR06VV9 on 2015-12-02
On that site right click in the outside of the game field in the white area and it will show you a option to enable the Java console.
UBlock Orirgin is a Add On if you have it just click on the Icon on your top Bar of the Browser.
I put a Screen shot to show UBlock.

---

### Post by kccv42 on 2015-12-02
I dont see the "enable java console". Attached is what i see?

---

### Post by QDR06VV9 on 2015-12-02
Installing OpenJDK 7 (optional)
To install OpenJDK 7, execute the following command:


```
sudo apt-get install openjdk-7-jre 
```
This will install the Java Runtime Environment (JRE). If you instead need the Java Development Kit (JDK), execute the following command:


```
sudo apt-get install openjdk-7-jdk
```

More Info here  [https://www.digitalocean.com/community/tutorials/how-to-install-java-on-ubuntu-with-apt-get](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-ubuntu-with-apt-get)

---

### Post by scoutchorton on 2015-12-02
What version/package of Java do you have installed? Go to the Ubuntu Software Center and search Java.

You may need a certain version of Java. If no packages are installed/with a green check mark, go to Terminal and type:

```
sudo apt-get install default-jre
```

If there is something installed, then come back and tell us what you got.

Good luck! :D

> **runrickus said:**
> Installing OpenJDK 7 (optional)
To install OpenJDK 7, execute the following command:


```
sudo apt-get install openjdk-7-jre 
```
This will install the Java Runtime Environment (JRE). If you instead need the Java Development Kit (JDK), execute the following command:


```
sudo apt-get install openjdk-7-jdk
```

More Info here  [https://www.digitalocean.com/community/tutorials/how-to-install-java-on-ubuntu-with-apt-get](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-ubuntu-with-apt-get)

Exactly. I ran it with Openjdk 7 and it worked, so this is the exact way to do it. runrickus, you beat me to the post :p

---

### Post by kccv42 on 2015-12-02
I did that and it still doesnt work.

---

### Post by QDR06VV9 on 2015-12-02
> **Caleb_Horton said:**
> Exactly. I ran it with Openjdk 7 and it worked, so this is the exact way to do it. runrickus, **you beat me to the post **:p
He He! Fastest fingers this side of the Rocky's:D
Thanks for the confirmation..
Kind Regards

> **kccv42 said:**
> I did that and it still doesnt work.

Huh? What? LOL
Did you restart your browser? And you are using chromium or crome Right? Just to be sure.

---

### Post by kccv42 on 2015-12-02
I am using ubuntu 14.0. Any suggestions?

I have been using chromium.

---

### Post by QDR06VV9 on 2015-12-02
What is the output of this in the terminal, Paste this back here
```
[COLOR=#333333][FONT=monospace]java -version[/FONT][/COLOR]
```

---

### Post by kccv42 on 2015-12-02
java runtime 8

---

### Post by QDR06VV9 on 2015-12-02
You need this one jdk
Just open your software manager(Synaptic or Software center)
Search for the java-jdk the same version you currently have and install that.
This is what mine shows
```
$ java -version
openjdk version "1.8.0_66"
OpenJDK Runtime Environment (build 1.8.0_66-b17)
OpenJDK 64-Bit Server VM (build 25.66-b17, mixed mode)

```

---

### Post by scoutchorton on 2015-12-02
Try doing this: 

```
sudo apt-get purge openjdk-7-jdk
```

then:

```
sudo apt-get purge openjdk-7-jre
```

By doing this, you uninstall Java, but purge also deletes configuration files.
This way, if you are like me and just roam around settings because of bordem, and you change something you shouldn't, this will delete that so when you do reinstall:

```
sudo apt-get install openjdk-7-jdk
```

and:

```
sudo apt-get install openjdk-7-jre
```

you get a fresh install even if you changed something you shouldn't have.

Hope this solves it, and good luck! May the code be with you! :D

---

### Post by kccv42 on 2015-12-03
This is what i get.

```
java version "1.7.0_91"
OpenJDK Runtime Environment (IcedTea 2.6.3) (7u91-2.6.3-0ubuntu0.14.04.1)
OpenJDK Client VM (build 24.91-b01, mixed mode, sharing)
```

---

### Post by QDR06VV9 on 2015-12-03
See if that works for now.
No never mind that should have installed this.
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install openjdk-8-jdk[/FONT][/COLOR]
```
So remove the openjdk-7-jdk
And install the newer version with command above.
Regards

---

### Post by kccv42 on 2015-12-03
It still doesnt work. I also dont have an option to enable java console. How do I do that?

---

### Post by QDR06VV9 on 2015-12-03
What addons do you have for chromium?

---

### Post by QDR06VV9 on 2015-12-03
Check to see if you have it enabled under Settings>Privacy> then there will be a tab that says Content Settings Click on that and navigate down to JavaSettings and tick the box that reads 
Allow all Sites to run Java.

---

### Post by kccv42 on 2015-12-03
It was already marked "allow all sites to run java" 
I still get this screen.

---

### Post by QDR06VV9 on 2015-12-03
You probably all ready know this but just to be sure, You navigate with the mouse and clicks.
But i get different options with a right click on the outside of the game field.

---

### Post by kccv42 on 2015-12-03
I dont have the javascript option that you have.

---

### Post by QDR06VV9 on 2015-12-03
:( That's not good..
Let me think some more. Oh and by the way did you uninstall the 1.07 version?

---

### Post by kccv42 on 2015-12-03
how do i uninstall that version. Can you give me a code?

---

### Post by QDR06VV9 on 2015-12-03
:D
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get purge openjdk-7-jdk[/FONT][/COLOR]
```
And to install the newer
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install openjdk-8-jdk[/FONT][/COLOR]
```

---

### Post by kccv42 on 2015-12-03
here is what i get 
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
E: Unable to locate package openjdk-8-jdk
computer@computer-Presario-CQ56-Notebook-PC:~$ 
```

---

### Post by QDR06VV9 on 2015-12-03
Please see this [http://sourcedigit.com/14692-install-openjdk-8-ubuntu-14-10-ubuntu-14-04-ubuntu-12-04-systems/](http://sourcedigit.com/14692-install-openjdk-8-ubuntu-14-10-ubuntu-14-04-ubuntu-12-04-systems/)
And i will be back in a moment.

---

### Post by kccv42 on 2015-12-03
I did that. Whats next?

```
openjdk version "1.8.0_45-internal"OpenJDK Runtime Environment (build 1.8.0_45-internal-b14)
OpenJDK Server VM (build 25.45-b02, mixed mode)
```

---

### Post by QDR06VV9 on 2015-12-03
Try the game..And see if you now have that option in the field oustside the game

---

### Post by kccv42 on 2015-12-03
I tried the game it doesn't work. The options don't show up when i right click.  only the options i see are inspect elements.

---

### Post by QDR06VV9 on 2015-12-03
Lets try this when you see this
[IMG]http://i.imgur.com/g3e0XHW.png[/IMG]

Just put your mouse and click on the [Continue] option.
More on the game here..[https://github.com/mmcnicol/StratConClone/wiki/Getting-Started](https://github.com/mmcnicol/StratConClone/wiki/Getting-Started)

---

### Post by kccv42 on 2015-12-03
I finally got it to work. Thanks alot. this a good game.

---

### Post by QDR06VV9 on 2015-12-03
You know I am not much of a gamer, But yes i seem to like it for now!
By the way I just saw this
> Dependenciesuse a web browser that supports HTML5 canvas.
License
GPL version 3
Works fine in Firefox also.
Cheers

---

