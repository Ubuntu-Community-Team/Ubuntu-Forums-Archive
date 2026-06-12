---
title: "Firefox Beta 3 Add-ons"
date: 2008-04-29
forum: General Help
---

### Post by sniffcrisps on 2008-04-29
Hi,  Upgraded to Ubuntu Hardy which ships with Firefox Beta 3.  None of my Add-ons are compatible.  When will they become usable?

---

### Post by Rainstride on 2008-04-29
when firefox 3 is officialy released most likly. i know how you feel though, i cant use my normal theme, or ext ether. atleast ad block and no script work.

---

### Post by sniffcrisps on 2008-04-29
It just amazes me that an LTS release would ship with a beta release as it's default browser.

---

### Post by howlingmadhowie on 2008-04-29
the extensions will get updated when the maintainers get round to doing so. with some extensions this means a long wait. other extensions however would work fine in firefox if they had their firefox version check updated. 

to see if an extension would work. [http://lifehacker.com/355973/make-your-extensions-work-with-the-firefox-3-beta](http://lifehacker.com/355973/make-your-extensions-work-with-the-firefox-3-beta) says the following:

    > * Type about:config into Firefox's address bar and click the "I'll be careful, I promise!" button.
    * Right-click anywhere. Choose New>Boolean. Make the name of your new config value extensions.checkCompatibility and set it to false.
    * Make another new boolean pair called extensions.checkUpdateSecurity and set the value to false.
    * Restart Firefox.

some extensions may be buggy, so watch out! :)

if firefox does go horribly wrong and crash when you try to start it with extensions enabled. start it as follows:

press alt+f2
enter the following: firefox -safe-mode

now firefox will start without extensions and you can experiment with which ones work or not

---

### Post by the-edmeister on 2008-04-29
> It just amazes me that an LTS release would ship with a beta release as it's default browser. They're saying the same thing over at MozillaZine.

---

### Post by phersotty on 2008-05-19
I made an interesting discovery...  After getting frustrated that I could not install my favourite Firebug add-on in Firefox 3 Beta 5, I opened up the Synaptic Package Manager and marked it for complete removal and installed Firefox 2.0.  After the downgrade I tried to install Firebug and this time I got an error that kept coming up no matter which extension I tried.  So I gave up and went back to Firefox 3 Beta 5.  While I was browsing through the Synaptic Package Manager I discovered that the Firebug extension was listed in the Synaptic Package Manager.  I marked it for installation and to my surprise it worked.  I now have Firebug working in Firefox 3 Beta 5 on Ubuntu 8.04 LTS.  I also found GreaseMonkey, Adblock Plus and Flashblock. 

So the point of my long winded post is ...

[SIZE="5"]Firefox 3 Beta 5 extensions can be found in the Synaptic Package Manager in Ubuntu 8.04 LTS !![/SIZE] :KS:popcorn::guitar:

**_Don't forget to restart Firefox_** after using the Synaptic Package Manager to load the new extensions

---

### Post by Coplen on 2008-05-19
> **sniffcrisps said:**
> It just amazes me that an LTS release would ship with a beta release as it's default browser.

Not me. Why use Firefox 2 when it dies this year?

---

### Post by vishzilla on 2008-05-19
Firefox 3 is way better than 2. Its only a matter of time the extensions would work in Fx 3. Its good that Hardy comes with Fx 3 as default. Within a month we will have the final version

---

