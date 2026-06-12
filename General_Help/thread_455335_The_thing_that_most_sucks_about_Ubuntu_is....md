---
title: "The thing that most sucks about Ubuntu is..."
date: 2007-05-26
forum: General Help
---

### Post by SlCKB0Y on 2007-05-26
No matter how hard I have tried with at LEAST the last few releases...

At least one and sometimes both the Azureus packages in the repos are broken. It's as simple as that and that is a basic thing.

Before any fanboys try to diss me I have have a degree in computer science, and have been using Linux EXCLUSIVELY for the past 11 years. Straight up azureus is totally busted and the gcj version is more than partially busted. It leaks memory like a sieve, the icons dont resize correctly and it occasionally takes X down. 

Please dont blame this on java or on azureus because every of linux distro and every other OS i have tried it on can get this to work.

Its pretty damn basic.

Get your **** together Ubuntu!!!

:)

---

### Post by rillip on 2007-05-26
Lots of people use it without issue all the time.  Sorry yours is broken.  Are you interested in fixing it?  From the tone of your post, it sounds like you just want to complain.

Sorry that something provided to you totally free has a bug on YOUR install/setup with ONE program is busted.  I'd ask for a refund if I was you.

Or maybe use one of these other distros you say works so well for you.

If you actually want help fixing it, you might try uninstalling, then download and reinstall.  If it's still the same, you know it's not the repos.  If it's better, you should probably post in the development forum and let them know so that the repos can be changed, either for the current versions or next.

---

### Post by KaroSHiv0n on 2007-05-26
With someone so high and mighty, you sure use a crap client.
Look on az not working for you as a gift and go use a client that wont munch away all your resources.

---

### Post by cyrusrayne on 2007-05-26
Looks like people need to be a little more respectful.  I would agree to try to download and reinstall it.  Another thing you might want to try is another client similar to Azureus or even reinstalling Ubuntu.  Those are all options that I have found prove very useful in fixing a problem.  Best of luck :)

---

### Post by stylishpants on 2007-05-26
One common problem is running Azureus with the wrong java.  It is an easy mistake to make because it usually runs, but badly and with more crashes.

Azureus needs Sun java 5 to run properly.  It is not enough to install the sun-java5-jre package either -- you need to configure the alternatives system to use Sun java 5 or you won't get it.

To see which java is being used by Azureus, check the About dialog in Azureus (Help->About).

To see which java is being supplied by the "java" command-line command:
```

fraser@ged:/tmp$ java -version
java version "1.5.0_11"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_11-b03)
Java HotSpot(TM) Client VM (build 1.5.0_11-b03, mixed mode, sharing)

```
My azureus runs flawlessly with this jre.

To specify which java to use:
```
sudo update-alternatives --config java
```

---

### Post by SlCKB0Y on 2007-06-04
> **KaroSHiv0n said:**
> With someone so high and mighty, you sure use a crap client.
Look on az not working for you as a gift and go use a client that wont munch away all your resources.

So what would you recommend? I have tried deluge and found it to unstable and lacking in features.

---

### Post by SlCKB0Y on 2007-06-04
> **stylishpants said:**
> One common problem is running Azureus with the wrong java.  It is an easy mistake to make because it usually runs, but badly and with more crashes.

Azureus needs Sun java 5 to run properly.  It is not enough to install the sun-java5-jre package either -- you need to configure the alternatives system to use Sun java 5 or you won't get it.

To see which java is being used by Azureus, check the About dialog in Azureus (Help->About).

To see which java is being supplied by the "java" command-line command:
```

fraser@ged:/tmp$ java -version
java version "1.5.0_11"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_11-b03)
Java HotSpot(TM) Client VM (build 1.5.0_11-b03, mixed mode, sharing)

```
My azureus runs flawlessly with this jre.

To specify which java to use:
```
sudo update-alternatives --config java
```

I thank you for your help rather than attitude like the other guys.

---

### Post by wulfhound on 2007-06-13
> **SlCKB0Y said:**
> No matter how hard I have tried with at LEAST the last few releases...

At least one and sometimes both the Azureus packages in the repos are broken. It's as simple as that and that is a basic thing.

Before any fanboys try to diss me I have have a degree in computer science, and have been using Linux EXCLUSIVELY for the past 11 years. Straight up azureus is totally busted and the gcj version is more than partially busted. It leaks memory like a sieve, the icons dont resize correctly and it occasionally takes X down. 

Please dont blame this on java or on azureus because every of linux distro and every other OS i have tried it on can get this to work.

Its pretty damn basic.

Get your **** together Ubuntu!!!

:)

Mine works fine....lol
:popcorn:

---

