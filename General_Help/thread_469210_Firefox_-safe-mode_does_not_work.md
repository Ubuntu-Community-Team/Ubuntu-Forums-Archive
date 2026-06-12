---
title: "Firefox -safe-mode does not work"
date: 2007-06-09
forum: General Help
---

### Post by ocumo on 2007-06-09
I am running Feisty, with all the updates. Firefox is 2.0.0.4. Recently, not sure exactly since when, but it seems to me that after the latest update of the Linux source and headers (2.6.20-16-generic), Firefox started behaving wrong: some crashes, and sometimes it will stop rendering urls from a web page that has been working for several minutes, i.e., I click in some link and it doesn't do anything, whereas I go to another tab and other website is working.

I tried **firefox -safe-mode** in the command line, but found that Firefox will start exactly the same as if I launch it normally, i.e., the extensions keep running. If I would type **firefox -anything** it will do exactly the same: just start normally, no error message. It would seem as if the script **firefox is not parsing the -safe-mode option**. In fact, I tried other option: **firefox -width 500** and it also starts just full screen, normally, completely ignoring the -width option.

I tried running the binary file directly:

```
/usr/lib/firefox/firefox-bin -save-mode
```


which doesn't help, it returns:

```
/usr/lib/firefox/firefox-bin: error while loading shared libraries: libmozjs.so: cannot open shared object
file: No such file or directory
```

which I take it means that firefox needs to be lauched via the firefox script /usr/lib/firefox/firefox

The extensions I have (last versions):
ScrapBook, DownloadHelper, DownThemAll, FlashGot, Greasemonkey and MouseGestures.

**My questions:**

Has anybody run successfully firefox -safe-mode in Feisty recently?
Any ideas what is going on? what is broken here: is this one of this [KXU]buntu things that I can't pass arguments to the firefox script normally and instead have to use some "special" [K]Ubuntu or Debian trick?

Many thanks in advance for any tips,

Ocumo

---

### Post by ocumo on 2007-06-09
**I think I may have found the reason why -safe-mode was not working.**

Typically, when Firefox crashes - or at least in many of the troubles commonly reported about Firefox - there is some firefox process instance that refuses to close. Now, it appears that firefox -safe-mode will not work if there would be any existing instance of firefox running.

Now, although I did close all the firefox windows before trying the -safe-mode option in the console, I did have a couple of crashes where the main window closed, and also a couple of situations where firefox stop working properly and I had to close it. This means, there is quite a big chance that I might have had a firefox process running when I tried the command in the console.

Since I opened and closed so many times the firefox application and its windows, it maybe that the crashed process that was running without a visible window died sometime, because I tried a several minutes ago doing

```
ps axjf | grep firefox
```


to make sure there was no firefox processes running, and then I tried


```
firefox -safe-mode
```


and this time safe mode worked.

**Moral: Before running **firefox -safe-mode , **make sure that there is not any other firefox process running, even if you have closed all the visible firefox windows.**

I hope that this explains the issue with -safe-mode and that there is nothing else broken except the original issues I saw in the first place.

It seems that at least I can now start troubleshooting the original problems with the standard procedure of running the safe mode.

Ocumo

---

