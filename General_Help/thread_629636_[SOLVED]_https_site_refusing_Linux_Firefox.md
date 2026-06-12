---
title: "[SOLVED] https site refusing Linux Firefox"
date: 2007-12-02
forum: General Help
---

### Post by Bobrm2 on 2007-12-02
I have a MS (XPpro) and a Unbunto 7.10 box. I am unable to login to my bank&#347; site while on the Ubuntu 7.10 box, both run Foxfire 2.0.0.10. have login to Mozilliazine and followed inst, to check for SSL/cache, etc. Can login while on the windows box. Have started to believe that my bank is refusing any operating other than MS. Can log into other https:// sites with out a problem. Can someone confirm the possibility? Is there a work around (have tried Ägent Switcher). Information appreciated.

Bob

---

### Post by SaltyCrak on 2007-12-02
just a thought, but have you tried installing internet explorer in wine and loggin in that way?

---

### Post by notoriousdbp on 2007-12-02
It's possible that could be the case but anyone who maintains a site like that should be fired as the site would be classed as not being accessible

---

### Post by handaxe on 2007-12-02
I encountered probs back with Firefox in Feisty with internet banking (that was the first appearance of the FF 2.0 series right? Os was it Edgy? Anyhow, it was with FF 2.0). However FF in Windows ALSO gave issue but IExplorer in Windows connected properly. When you connect fine in Windows is it with IE or FF?

I enabled ssl2 among others in about:config in FF. Is that what you refer to as the advice from Mozilla?

HA

---

### Post by Bobrm2 on 2007-12-02
Connected with the old BOOKMARK, sorry for the caps, I havent figured how to change the fonts that would allow a colon, anyway, with the old BMs I could make a connection in Thunderbird, never had problems with IE. Now, I can enter the new url in the address bar and make the connection (in FF), this is on the Windows machine.

I have yet to be successful on the Ubuntu 7.10, attempting the connection with Firefox and Epiphany browsers.

Bob

---

### Post by Bobrm2 on 2007-12-02
sorry about that (Thunderbird) should read Firefox.

---

### Post by handaxe on 2007-12-02
... and ssl2 is enabled in about:config, as well as  security.ssl3.rsa_rc4_40_md5 = true?

HA

PS Use the edit function to change a message rather than post a correction...

---

### Post by irish_flu on 2007-12-02
If you think that they're actively blocking you because you're not using Windows, you could try the "User Agent Switcher" add-on for Firefox.
[https://addons.mozilla.org/en-US/firefox/addon/59?id=59&vid=617](https://addons.mozilla.org/en-US/firefox/addon/59?id=59&vid=617)

You can configure it to tell websites you're using Internet Explorer on Windows Vista, if you like.

---

### Post by handaxe on 2007-12-02
I could accept a bank that blocked you because they believed it was for the best (even if bullsh*t) BUT at least informed you hat they were. Invisibly blocking you is a no no, no?

But it is a thought - do you have pop ups disabled for that site and thus miss an info pop-up?

HA

---

### Post by Trebaruna on 2007-12-02
I would recommend sending them a friendly email asking them whether they are actively refusing connections from Linux boxes, and whether they have any plans to support their customers who choose Linux.
This will do two things: tell you what is happening (perhaps even get you some support) and let them know people want Linux support.

---

### Post by Bobrm2 on 2007-12-02
> **handaxe said:**
> ... and ssl2 is enabled in about:config, as well as  security.ssl3.rsa_rc4_40_md5 = true?

HA

PS Use the edit function to change a message rather than post a correction...

I have set to true or enabled both. Closed and reopened FF, but no change. Will continue reading down the replies.

Bob

---

### Post by Bobrm2 on 2007-12-02
> **irish_flu said:**
> If you think that they're actively blocking you because you're not using Windows, you could try the "User Agent Switcher" add-on for Firefox.
[https://addons.mozilla.org/en-US/firefox/addon/59?id=59&vid=617](https://addons.mozilla.org/en-US/firefox/addon/59?id=59&vid=617)

You can configure it to tell websites you're using Internet Explorer on Windows Vista, if you like.


I forgot to mention that I had configured Agent Switcher, for this website.  Since, at one time the windows box would not connect to the url, I suspect it , the problem, has to do with configuration??

---

### Post by handaxe on 2007-12-02
In one thread on this topic, a user wrote that they enabled all the security options in about:config.  Worth a shot.  

If that does not work, then the other advice applies: find out if they block anything other than IE.  If they do, change banks on principle and tell them why you are doing so.

HA

Ps Am editing in response to your reply (unseen at time of writing).  Definitely contact the bank and ask.... if Windows struggled at some point then some config issue is very likely,

---

### Post by Bobrm2 on 2007-12-02
> **handaxe said:**
> I could accept a bank that blocked you because they believed it was for the best (even if bullsh*t) BUT at least informed you hat they were. Invisibly blocking you is a no no, no?

But it is a thought - do you have pop ups disabled for that site and thus miss an info pop-up?

HA

Justed checked and Popups have been allowed since way back?

---

### Post by froy02 on 2007-12-02
I do not have a problem logging in to wellsfargo, bank of america nor american expressusing firefox either in XP or ubuntu.

---

### Post by DugieHowsa on 2007-12-07
I am having a similar problem logging into citizens bank ( [http://www.citizensbank.com/](http://www.citizensbank.com/) ).  Once I click on the Login button.  It just hangs.  It seems to be having a problem with the javascript redirecting to the https site.  I also have the user agent switch plug-in installed and it does not help the situation.  I also have to say I have been having this problem ever since I upgraded to Gutsy.

---

### Post by Bobrm2 on 2007-12-08
My bank has laied the problem to software compatibility issues. I thought that maybe it has to do with JAVA, but latest JRE 1.6.0.xxx is installed. Have compared settings between the two machines, (XPpro/Unbuntu Gutsy). SSL 3.x and TTL 1.x. Continue to seek an answer. 

Bob

---

### Post by DugieHowsa on 2007-12-15
Finally... it looks like everything is now working.

First, I went to the about:config page in firefox and set the following value to true:

plugin.expose_full_path

Next, I went back to the about:plugins page in firefox.

Upon further review, I found that I had 2 instances of java plugins, both trying to execute from different directories.

The official Ubuntu sun-java6 binaries are installed in /usr/lib/jvm . I deleted the other java directory from my machine.

I then confirmed that all the java plugin links were pointing to the remaining java plugin binary.  This included the following:

```

/usr/lib/mozilla/plugins/libjavaplugin_oji.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
/usr/lib/mozilla/plugins/libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so

/usr/lib/firefox/plugins/libjavaplugin_oji.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
/usr/lib/firefox/plugins/libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so

/etc/alternatives/firefox-javaplugin.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
/etc/alternatives/mozilla-javaplugin.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

```

Finally, I restarted firefox, and went back to the about:plugins page to confirm there was only one instance of the java plugin installed.  Upon revisting the Java test pages, the java plugin was recognized successfully.

---

### Post by Bobrm2 on 2007-12-15
I ran a search for sun-java6, with a return of 49 files. None reside in /usr/lib/jvm. Not being familiar with Linux I wonder if I should just delete 49 files and return to Synaptic with a reinstall; however there are many files that I do not know which to reinstall. Where can I gather further information about which files to keep and which to disregard. Thanks

Bob

---

### Post by Bobrm2 on 2007-12-16
**Upon further review, I found that I had 2 instances of java plugins, both trying to execute from different directories.**

Not reading your post as I should have; however upon reading I discovered the above comment. Never understood there is a page about:config. In anycase there is no mention of JAVA anywhere on the page??  Will look into that now.

Bob

---

