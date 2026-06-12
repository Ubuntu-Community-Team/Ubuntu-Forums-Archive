---
title: "How do I flush the cache in Ubu 16.04"
date: 2016-12-08
forum: General Help
---

### Post by pedro_rodriguez2 on 2016-12-08
I am having trouble on this laptop logging into chinese.stackexchange.com I can log in from an older laptop. So I thought the problem is specific to this computer. However, on a desktop computer at work, running Fedora 23, I experienced exactly the same problem. 

I deleted all cookies.
I want to flush the cache: I tried: 

> pedro@pedro-275E4E-275E5E:~$ sudo network-manager restart
sudo: network-manager: command not found

No joy. How do I flush the dns cache in Ubu 16.04?

Also, how can I check that java is working and has not been disabled?

Thanks!

---

### Post by DuckHook on 2016-12-08
Restarting network manager is an odd way to do what you are trying to do. In fact, it is not a fruitful tactic. The following recent thread has a relevant method: [https://ubuntuforums.org/showthread.php?t=2342883](https://ubuntuforums.org/showthread.php?t=2342883) As per that thread, are you sure the problem is the DNS cache?

And the usual way to check for *any* running process is:```
ps -ef | grep name_of_process
```

---

### Post by pedro_rodriguez2 on 2016-12-08
Not sure about anything. Maybe I have unintentionally disabled javascript in Firefox. Not sure how to check that either. As I hardly ever use Chrome, I don't think I would have disabled javascript there. This happened shortly after the latest update to the latest kernel. I tried booting with an older kernel. Did not help. I also started Ubu 14.04, same problem on this laptop. No log in to chinese.stackexchange.com

```
pedro@pedro-275E4E-275E5E:~$ ps -ef | grep java
pedro     7538  7509  0 14:45 pts/2    00:00:00 grep --color=auto java
pedro@pedro-275E4E-275E5E:~$ 
```

java is found, (I think)

The strange thing is, I have this problem on Ubuntu 16.04 and Fedora 23, on 2 different computers, but on my old laptop, with Ubu 16.04, it works, no problem, I can log in!

---

### Post by DuckHook on 2016-12-09
> **pedro_rodriguez2 said:**
> Not sure about anything. Maybe I have unintentionally disabled javascript in Firefox. Not sure how to check that either.Java and Javascript are two entirely different animals. If you don't need Java, don't install it. However, java*script* is part of a default FF install. Many sites will not work without it. If it were not enabled, you would definitely notice it even after moderate browsing. Why are you asking about this? Did you disable javascript at some time, and now wish to enable it again? Do you have *noscript* (or similar) installed? Instructions for enabling/disabling: [http://kb.mozillazine.org/JavaScript](http://kb.mozillazine.org/JavaScript)

Also: "Javascript is not Java" [http://kb.mozillazine.org/JavaScript_is_not_Java](http://kb.mozillazine.org/JavaScript_is_not_Java)
> This happened shortly after the latest update to the latest kernel. I tried booting with an older kernel. Did not help. I also started Ubu 14.04, same problem on this laptop. No log in to chinese.stackexchange.comHave you tried purging FF's cache? [https://support.mozilla.org/en-US/kb/how-clear-firefox-cache](https://support.mozilla.org/en-US/kb/how-clear-firefox-cache)

While you are at it, also clear the cookies.
> java is found, (I think)Java was not found. In fact, your output confirms that Java is not on your system. This is as it should be. *You do not want Java installed.*

The *ps* command returns *all* processes with "java" in the process line. But this will include the search process itself, and since you searched for "java":```
ps -ef | grep ***java***
```…the search process will always show up as part of *ps*.> The strange thing is, I have this problem on Ubuntu 16.04 and Fedora 23, on 2 different computers, but on my old laptop, with Ubu 16.04, it works, no problem, I can log in!As suggested, try clearing your cache and cookies.

---

### Post by pedro_rodriguez2 on 2016-12-09
Thanks for your comments.

I discovered that if you enter about:config in Firefox, you can enable or disable javascript. It is enabled. I need java. I have jdkjava installed. I have a program called FormReturn, which runs entirely on java.  I use it a lot.

I discovered too that I can empty the cache and all cookies in Firefox>Preferences, which I did. The problem persists. 

Personally, I think stackexchange changed something. Their support told me their page loads AJAX and if google is blocked, nothing will work. I live in China, google is permanently blocked by the govt, but stackexchange was working till 2 days ago, and still works on my other laptop. Support is not always up to scratch.

I can still access their site on my old laptop, which runs Ubu 16.04, just the same as this one. 

Weird! I hope maybe the next system update will get rid of the problem.

---

### Post by DuckHook on 2016-12-09
> **pedro_rodriguez2 said:**
> I need java. I have jdkjava installed. I have a program called FormReturn, which runs entirely on java.  I use it a lot.My mistake. I must learn to stop jumping to conclusions. :redface:

I must also correct a previous error of mine. You actually *may* have Java installed. The various java implementations do not all have "java" in their name. If, for example, the actual process name is *jre*, then the *ps* command that you used would not show it. Using ps assumes that you have some idea of the actual process name. I don't use java, so am not the best person to help you here.> I discovered too that I can empty the cache and all cookies in Firefox>Preferences, which I did. The problem persists. 

Personally, I think stackexchange changed something. Their support told me their page loads AJAX and if google is blocked, nothing will work. I live in China, google is permanently blocked by the govt, but stackexchange was working till 2 days ago, and still works on my other laptop. Support is not always up to scratch.

I can still access their site on my old laptop, which runs Ubu 16.04, just the same as this one. 

Weird! I hope maybe the next system update will get rid of the problem.I can't help you with issues arising from behind the great firewall. Don't know enough about it. Am frankly spooked by it. Sorry to be of such limited assistance.

---

### Post by pedro_rodriguez2 on 2016-12-10
Thanks for trying, see how this pans out after a couple of updates. If it is still like that, maybe I'll do a reinstall, see it that clears it up.

---

