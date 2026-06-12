---
title: "Speed up Libreoffice start time"
date: 2022-07-03
forum: General Help
---

### Post by ubname on 2022-07-03
Hi, I'm using Libreoffice snap on Ubuntu 22.04 and it takes not less than 10 seconds to start,
is there any way to preload Libreoffice snap or to speed up statup time?
The problem is that any time you start it it will be slow, not only the firs time.

thanks

---

### Post by The Cog on 2022-07-03
You can uninstall that snap silliness and download a .deb installer from [https://www.libreoffice.org/download/download/](https://www.libreoffice.org/download/download/).

---

### Post by Autodave on 2022-07-03
Switching ti an SSD will help a bunch.

---

### Post by ubname on 2022-07-03
I'd prefer to use snap, I'm not willing to manage updates, and already am using ssd,
still hope for some help about my original question

---

### Post by pantazi on 2022-07-04
I have need for only Libre Office Writer. This starts instantly but is not a snap.

---

### Post by TenPlus1 on 2022-07-04
LibreOffice is already part of an Ubuntu installation using .deb's from the repository, and those run pretty quick.  Why replace them with a snap ?

---

### Post by Crimple on 2022-07-04
> **ubname said:**
> still hope for some help about my original question
It's in the hands of the Ubuntu devs.

---

### Post by kurt18947 on 2022-07-04
> **The Cog said:**
> You can uninstall that snap silliness and download a .deb installer from [https://www.libreoffice.org/download/download/](https://www.libreoffice.org/download/download/).

I had trouble with LibreOffice 7.3.x installed via snap on 20.04.x . I didn't really notice a slow startup after the first time but it was REALLY slow opening a password protected file from a USB3 thumb drive, several seconds to open a simple one page file. It also didn't show the flash drive as a source or destination, I had to open the file via Nautilus. I uninstalled the snap version and installed the flatpak version. That opened as expected and opened the file from a flash drive just like a .deb install. It also showed the flash drive as a read/write destination as expected. Updates and patches on apps installed via Flatpak seem to update as expected. Flatpak and snap can coexist peacefully, one does not interfere with the other. The snap version of LibreOffice in my 22.04 install works as expected, removable devices are seen as read/write and no excessive slowness opening. 

Canonical has been known to release technologies before they're fully mature, that may be the case with snap. Of course waiting until an app is perfect to release might be fine but it's obsolete by the time it's 'perfect' and another app has claimed the market space.

---

### Post by DuckHook on 2022-07-05
> **TenPlus1 said:**
> LibreOffice is already part of an Ubuntu installation using .deb's from the repository, and those run pretty quick.  Why replace them with a snap ?
&#8593;+1

@OP:
The problem with slow snap apps is not in the apps, but in snapd itself. It takes ages for snapd to initialize an app. It then takes additional ages for it to access locations that it considers non&#8209;standard (like USB drives). I don't know why snapd is so slow. The devs are [aware of this problem]("https://www.omgubuntu.co.uk/2022/05/ubuntu-making-firefox-snap-app-faster") and are working on it. This may bode well for improvement in the future, but it doesn't help you right now.

My question is the same as The Cog's: why use the snap version? I did read your reply: You're not willing to manage updates, but snaps must also be updated, so this is not really any different than installing the standard repo version:```
sudo apt install libreoffice
```If you insist on the absolute latest and greatest version, then Libreoffice is one of the few apps that I recommend using the PPA:```
sudo add-apt-repository ppa:libreoffice/ppa
```
Libreoffice updates will then occur as part of your normal system updates and are no more bothersome than snap updates&#8212;probably even less bothersome since you have finer control over the process.

For my part, like TenPlus1, I'm happy with the repo version, even if it's a bit behind the bleeding edge.

---

### Post by mIk3_08 on 2022-07-05
> **ubname said:**
> I'd prefer to use snap, I'm not willing to manage updates, and already am using ssd,
still hope for some help about my original question 
For me its better to try another package manager. Maybe its the answer to your issue. Regards and cheers.

---

### Post by ubname on 2022-07-09
> **TenPlus1 said:**
> LibreOffice is already part of an Ubuntu installation using .deb's from the repository, and those run pretty quick.  Why replace them with a snap ?

Hi, the .deb install does not work properly, i have IT localization and is the libreoffice package "deb" spell check does not work,
in the snap package it's working and that's why I'm using the snap package.

---

### Post by ubname on 2022-07-09
> **DuckHook said:**
> &#8593;+1

@OP:
The problem with slow snap apps is not in the apps, but in snapd itself. It takes ages for snapd to initialize an app. It then takes additional ages for it to access locations that it considers non&#8209;standard (like USB drives). I don't know why snapd is so slow. The devs are [aware of this problem]("https://www.omgubuntu.co.uk/2022/05/ubuntu-making-firefox-snap-app-faster") and are working on it. This may bode well for improvement in the future, but it doesn't help you right now.

My question is the same as The Cog's: why use the snap version? I did read your reply: You're not willing to manage updates, but snaps must also be updated, so this is not really any different than installing the standard repo version:```
sudo apt install libreoffice
```If you insist on the absolute latest and greatest version, then Libreoffice is one of the few apps that I recommend using the PPA:```
sudo add-apt-repository ppa:libreoffice/ppa
```
Libreoffice updates will then occur as part of your normal system updates and are no more bothersome than snap updates—probably even less bothersome since you have finer control over the process.

For my part, like TenPlus1, I'm happy with the repo version, even if it's a bit behind the bleeding edge.

Yes, sadly the deb package is not working properly ...

---

### Post by kurt18947 on 2022-07-09
> **TenPlus1 said:**
> LibreOffice is already part of an Ubuntu installation using .deb's from the repository, and those run pretty quick.  Why replace them with a snap ?

The version of Libre Office in the repositories may well be an older version. Sometimes that matters - MS Office compatibility for one - and sometimes it doesn't.

---

### Post by Holger_Gehrke on 2022-07-09
> **ubname said:**
> Hi, the .deb install does not work properly, i have IT localization and is the libreoffice package "deb" spell check does not work,
in the snap package it's working and that's why I'm using the snap package.

LibreOffice uses the package "hunspell" for spellchecking. Try installing hunspell-it (Italian dictionary for hunspell) and hyphen-it (Italian hyphenation rules) and possibly mythes-it (Italian thesaurus). You might have to add these dictionaries in "Tools"->"Option"->"Language Settings"->"Writing Aids".

Holger

---

### Post by DuckHook on 2022-07-09
> **Holger_Gehrke said:**
> LibreOffice uses the package "hunspell" for spellchecking. Try installing hunspell-it (Italian dictionary for hunspell) and hyphen-it (Italian hyphenation rules) and possibly mythes-it (Italian thesaurus). You might have to add these dictionaries in "Tools"->"Option"->"Language Settings"->"Writing Aids".

Holger

&#8593; A big +1 &#8593;

More specifically:```
sudo apt install libreoffice hunspell-it hyphen-it mythes-it
```Then, from within Libreoffice, as per Holger's instructions: "Tools"->"Option"->"Language Settings"->"Writing Aids".

---

### Post by aug7744 on 2022-07-09
The best option is use the PPA from reply above.
Load Writer in 8 secs in HDD SATA2

---

### Post by DuckHook on 2022-07-09
> **aug7744 said:**
> The best option&#8230;
It's worthwhile to note that the "best" option doesn't really exist. Like most things in life, it is relative and depends on all sorts of mitigating factors like use case, risk tolerance, ease of use, Linux knowledge and, not least, patience.

[LIST]
[*]The standard repo version has the advantage of being stable. Because it is in the Universe repo, it has been vetted by a trusted source and is almost guaranteed to work with its associated release. However, it will not be updated and will therefore also be guaranteed to fall behind with each Libreoffice update.
[*]The snap version has the advantage of being current. It is maintained by its snap author who may (or may not) be the Libreoffice devs. It has the additional advantage/disadvantage of being sandboxed by snapd, which increases security at the cost of constrained usage and will sometimes shade over into outright breakage. Snaps are also slow to start and sometimes just excruciatingly slow to run. I'm not sold on snap apps for these reasons: snapd is not really ready for prime time yet&#8212;but that is a purely personal conclusion.
[*]The PPA version has the advantage of both currency and no system constraints. But it suffers from the serious shortcoming that all PPAs share: it is a big and scary security hole. Installing PPAs is basically giving unknown and untrusted strangers complete access to root. Malware and bugs (so serious that they may as well be malware) have been shoehorned into Ubuntu through PPAs. It's a highly risky thing to do.
[/LIST]
It is past time to note that many new users come to Linux expecting easy, canned answers to life's complicated problems. Unfortunately, there are no such answers. Every choice involves a trade&#8209;off that enhances some advantages at the cost of increasing some concurrent drawbacks.

If this were my call, I would go with the standard repo version with the addition of the Italian spell-checker, hyphenator and thesaurus. That's the safest and stablest choice, and the lagging versions are not really a big deal. Using the standard and proven repo apps, I've never felt that I've missed out on the latest bells and whistles.

---

### Post by ubname on 2022-07-10
> **Holger_Gehrke said:**
> LibreOffice uses the package "hunspell" for spellchecking. Try installing hunspell-it (Italian dictionary for hunspell) and hyphen-it (Italian hyphenation rules) and possibly mythes-it (Italian thesaurus). You might have to add these dictionaries in "Tools"->"Option"->"Language Settings"->"Writing Aids".

Holger

Thanks, installing those packages worked.

---

### Post by ubname on 2022-07-10
> **DuckHook said:**
> &#8593; A big +1 &#8593;

More specifically:```
sudo apt install libreoffice hunspell-it hyphen-it mythes-it
```Then, from within Libreoffice, as per Holger's instructions: "Tools"->"Option"->"Language Settings"->"Writing Aids".

Yes this works, those packages should be automatically installed based on system localization IMHO.

---

### Post by ActionParsnip on 2022-07-10
If you also disable the java plug in if you don't use it, this can help. You can also tweak ram allocation to Libreoffice and how many undo steps you want. This can speed it up as well.

---

### Post by DuckHook on 2022-07-10
> **ubname said:**
> …those packages should be automatically installed based on system localization IMHO.
It's a good general idea, but many multilingual users change localization with some frequency. Moreover, many install using the default locale and only change localization afterwards. Libreoffice cannot detect the change.

---

### Post by DuckHook on 2022-07-10
FYI, though not strictly LibreOffice, this related topic bodes well for better future startup times in all snap apps: [https://www.omgubuntu.co.uk/2022/07/firefox-snap-significant-startup-improvements](https://www.omgubuntu.co.uk/2022/07/firefox-snap-significant-startup-improvements)

---

### Post by Holger_Gehrke on 2022-07-10
> **DuckHook said:**
> It's a good general idea, but many multilingual users change localization with some frequency. Moreover, many install using the default locale and only change localization afterwards. Libreoffice cannot detect the change.

Not only that. You'd need to have some kind of variable dependencies for that, along the lines of 'libreoffice-writer depends on hunspell-%language-code of chosen default language%'. AFAIK there's no way to have that with deb packages. In snap they simply pack a lot of the languages in, problem solved at the expense of a (much) bigger package.

Holger

---

### Post by aug7744 on 2022-07-10
PPA is from Libreoffice devs. Not problem with security.
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
sudo apt-get purge -y fonts-opensymbol* libjuh-java* libjurt-java* libridl-java* libuno-* libunoloader-java* python3-uno* uno-libs-private* ure*
sudo apt-get autoremove
sudo apt-get install libreoffice
if even thus has any issues
sudo apt-get --fix-broken install

---

### Post by DuckHook on 2022-07-11
> **aug7744 said:**
> PPA is from Libreoffice devs. Not problem with security.
I addressed this:> **DuckHook said:**
> &#8230;If you insist on the absolute latest and greatest version, then Libreoffice is one of the few apps that I recommend using the PPA&#8230;
> **aug7744 said:**
> sudo apt-get --fix-broken install
I neglected to mention that another serious problem with PPAs is their propensity to break *dpkg* through the installation of/requirement for incompatible dependencies. These forums are filled with threads from people seeking help for broken systems due to the addition of PPAs.

```
sudo apt-get --fix-broken install
```&#8230;should never be necessary except as a last resort and certainly should not be invited into the system on purpose.

There are other problems with PPAs besides security.

---

### Post by #&amp;thj^% on 2022-07-11
> **DuckHook said:**
>  These forums are filled with threads from people seeking help for broken systems due to the addition of PPAs.


+1 Sad but True, far to many problems associated with PPA's in the Forums.
Maintainers take heed. :( >>(Personal challenge to do Better)

---

