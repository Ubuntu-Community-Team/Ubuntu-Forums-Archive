---
title: "Firefox doesn't work after upgrade"
date: 2013-06-28
forum: General Help
---

### Post by tschill on 2013-06-28
I run Ubuntu 12.04 as a dual-boot with Windows. I use the Windows profile for the Ubuntu version of Firefox and Thunderbird. Yesterday Firefox was upgraded to 22. During the Add-on check Firefox stopped working. Since then Firefox doesn't download any websites any more. 

It is not a problem of the internet connection, Thunderbird and Chrome work fine.
Firefox under Windows, using the same profile, works without problem. 
Firefox under Ubuntu with the default Ubuntu profile works without any problems. 
I marked Firefox under Ubuntu for re-installation and applied it, the problem is still present.

So the problem lies somewhere in the shared profile and it doesn't influence the Windows Firefox performance. 

When starting Firefox under Ubuntu from a terminal using the Firefox profile manager and using the shared Windows/Ubuntu profile, then I get the following error message:

> firefox -profilemanager
error: proxmate: An exception occurred.
SyntaxError: JSON.parse: unexpected end of data
resource://jid1-qphd8urtzwjc2a-at-jetpack/proxmate/lib/main.js 64
Traceback (most recent call last):
  File "resource://gre/modules/commonjs/sdk/net/xhr.js", line 130, in 
    self._orsc.apply(self, arguments);
  File "resource://gre/modules/commonjs/sdk/request.js", line 93, in onreadystatechange
    emit(target, 'complete', response);
  File "resource://gre/modules/commonjs/sdk/event/core.js", line 83, in emit
    for each (let item in emit.lazy.apply(emit.lazy, arguments)) {
  File "resource://gre/modules/commonjs/sdk/event/core.js", line 106, in lazy
    try { yield listeners[index].apply(target, args); }
  File "resource://jid1-qphd8urtzwjc2a-at-jetpack/proxmate/lib/main.js", line 205, in exports.main/loadExternalConfig/<.onComplete
    createPacFromConfig(config);
  File "resource://jid1-qphd8urtzwjc2a-at-jetpack/proxmate/lib/main.js", line 64, in exports.main/createPacFromConfig
    config = JSON.parse(config);

Any suggestions how to get rid of this error is much appreciated, because I am not very familiar with Ubuntu.

---

### Post by tschill on 2013-06-28
Sorry, I forgot to mention that after "Restart with add-ons disabled..." the problem still exists. So not an add-on problem, I assume.

---

### Post by Impavidus on 2013-06-29
Has the windows firefox also been updated to 22?

---

### Post by tschill on 2013-06-29
Yup. In Windows Firefox is also version 22. 

From the mozilla forum I got the suggestion, to use the reset function which can be accessed from the "Troubleshooting Information" site or during the "Restart with all add-ons disabled". This left me with a virgin profile folder, because this process deleted the information from the shared profile (which is on the Win partition), deleted the entry for this profile in  Ubuntu's Firefox profile manager and created another, new profile in Ubuntu's Firefox profile folder. 

Luckily I made a copy of the shared profile to restore the old version, but of course the problem still exists - Firefox in Ubuntu doesn't load any website, when using the Win/Ubuntu shared profile. What I don't understand: It is clearly a profile problem, using any other profile in Ubuntu works perfectly well. But in Windows, using exactly the same shared profile, loading websites doesn't create any problems. Mysterious.

---

### Post by tschill on 2013-06-29
I followed now the suggestion from the Mozilla community:

I used the [FEBE add-on]("https://addons.mozilla.org/en-US/firefox/addon/febe/") to backup my old settings, add-ons and preferences. I renamed my shared folder and created a new folder with the same name, to which I linked the UBUNTU Firefox profile manager. Then I re-imported with FEBE my settings and add-ons. Now I have to re-configure the add-ons, but it is still faster than to search for the file in the old profile, which causes the problem. So far, it works on Ubuntu and Windows without problem.

---

### Post by bayouoldguy on 2013-07-04
Also had update to Firefox v22......Just saw bug report on my Ubuntu updater, did not install the fix yet, kind of waiting for someone else to take the lead !!!....G

Ubufox Extension problem, Ubuntu 12.04 
Just had a big problem while browsing the net. Lost all Firefox toolbars & could not get them back. After uninstalling, re-installing Firefox among other things, I uninstalled the
Ubufox extension ( xul-ext-ubufox 2.6-0ubuntu0.12.04.1 ), & rebooted; cleared up the lost toolbars, etc. by having a simple Firefox. Is anyone else experiencing similar problems ?. I
usually keep this Dell D620 up to date thru the Ubuntu updater, so maybe the last change or so blew something out !!!!!......G

---

### Post by Mark Phelps on 2013-07-04
I would not use FF v22 at this point.  

On my Windows OS, FF automatically upgraded to v22 -- and after careful testing, I discovered that upgrade was the reason for certain window elements not being displayed properly anymore.  I uninstalled FF v22, reinstalled FF v21, and the display elements are back to normal.

---

