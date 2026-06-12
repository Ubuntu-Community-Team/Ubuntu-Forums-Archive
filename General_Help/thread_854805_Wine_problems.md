---
title: "Wine problems"
date: 2008-07-09
forum: General Help
---

### Post by upshutdown on 2008-07-09
First off, i managed to install Steam with wine with just about no problem.
I am able to load up steam as normal but when steam logs in Wine gives me this error
"This application is trying to show an HTML page. Wine needs Gecko...Click install if you want Wine to automatically install Gecko"
so naturally i click install. After install everything closes. I restart steam, log in again, then i get the same error message telling me to install Gecko. Ive tried restarting X, didnt help. 
Any help would be greatly appreciated with this.

Second im trying to setup World of warcraft on my machine. I copied it over from my Windows partition. I did:

cd (WoW folder)
wine WoW.exe

And then it gives me this output
```
~/Desktop/World of Warcraft$ wine wow.exe
fixme:advapi:SetSecurityInfo stub
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\common.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x32eda4,0x00000000), stub!
X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  148 (GLX)
  Minor opcode of failed request:  16 (X_GLXVendorPrivate)
  Serial number of failed request:  507
  Current serial number in output stream:  508

```

if im being a total noob let me know, still pretty new with Linux in general so...a general guide in the correct direction would be appreciated as well.

---

### Post by Taxman415a on 2008-07-09
I don't know anything about the WoW issues, but for the Steam problem, try installing gecko before running Steam by installing winetricks and using it to install gecko. See the instuctions here:
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

basically after getting winetricks you'd run
```
sh winetricks gecko
```

and it looks like from here [http://developer.valvesoftware.com/wiki/Steam_under_Linux#Installing_required_fonts](http://developer.valvesoftware.com/wiki/Steam_under_Linux#Installing_required_fonts) that you need to install the Tahoma font.

For the WoW try googling various combinations of WoW, linux, wine, and Ubuntu should get you enough instructions to get it working. Also googling for your specific error message can work. Those are just general tips to get you out of newb land :)

---

### Post by upshutdown on 2008-07-09
ahh yess...thank you...that totally fixed my steam problem :)) CSS here i come

now i want to get rid of windows altogether, so if anyone could help with the WoW problem that would be great...have been doing the whole google thing for a bit too long.

---

### Post by Taxman415a on 2008-07-10
Gald to hear you got one working!

Hmm, based on this: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922)  WoW should install and run really well. What version of Ubuntu, Wine, and Wow are you running?  If you're running Hardy you could always try the instructions here [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb) for installing the latest version of wine. It's not recommended exactly, and make sure to tell people that's what you did if you have problems, but it may help. Your other option is to post your problem directly on the pages at the appdb at winehq for your specific WoW version. Just make sure to specify your wine and Ubuntu version. I think they'll pretty much tell you to upgrade your wine to the newest release anyway though.

---

