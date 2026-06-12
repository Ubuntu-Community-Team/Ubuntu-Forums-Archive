---
title: "After updates Firefox wont run, even in safe mode."
date: 2017-01-03
forum: General Help
---

### Post by philinux on 2017-01-03
Tried reinstalling, new profile. Tried reinstalling mate core and mate desktop.

Running from terminal gives.
```
Generated clone child 6003
sendcontinuesignaltochild send continue signal to child
waitforcontinuesignal wait for continue signal

```
Then crash notifier window pops up.

Anyone got any ideas to try. Also Software Boutique wont run either.

Tried midori and epiphany both crash as well.
Also tried booting from previous kernal.

---

### Post by dragonfly41 on 2017-01-03
Same scenario reported here ...

[http://askubuntu.com/questions/858540/firefox-crashes-immediately-on-start-up/859497](http://askubuntu.com/questions/858540/firefox-crashes-immediately-on-start-up/859497)

---

### Post by philinux on 2017-01-04
Yes it's similar but no solution.

---

### Post by Keith_Helms on 2017-01-04
You could try a newer version
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

or remove it and manually install an older version
[https://ftp.mozilla.org/pub/firefox/releases/](https://ftp.mozilla.org/pub/firefox/releases/)

If those don't work, then I'd guess you have some hardware or software problem outside of Firefox.

---

### Post by philinux on 2017-01-07
Thanks Keith I'll try both when i'm next down at my mates.

Odd other browsers wont run either and software boutique fails to run. Might have to reinstall as last resort.

---

### Post by yoramdavid on 2017-02-06
I am having the same problem on an old computer where I just installed a new system.
I get the same error (or very similar, see below) as you do.

Are you on an old computer as well? I read a [threat]("https://support.mozilla.org/gl/questions/1153419") where they think it could be due to the processor being too old for the newer version of flash.

They suggest to downgrade flash.

In my case, Thunderbird does not work either, nor does Chromium web browser.

> ExceptionHandler::GenerateDump cloned child 2934
ExceptionHandler::SendContinueSignalToChild sent continue signal to child
ExceptionHandler::WaitForContinueSignal waiting for continue signal...
ExceptionHandler::GenerateDump cloned child ExceptionHandler::WaitForContinueSignal waiting for continue signal...
3014
ExceptionHandler::SendContinueSignalToChild sent continue signal to child

---

### Post by philinux on 2017-03-13
Update.

Firefox working now after the latest updates. Software boutique still not working and other available browsers crash. But lifespan of i386 olds pc still going.
Not using flash either.

---

