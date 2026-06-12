---
title: "pidgin spellcheck"
date: 2007-09-30
forum: General Help
---

### Post by Chymera on 2007-09-30
ok, so how do i get pidgin to check spelling for other languages than English?

---

### Post by Chymera on 2007-10-05
bump...

---

### Post by holscher on 2007-10-15
you hve to install the purple-plugin-pack...
if you are using feisty you can find the package here: [http://download.ubuntu.pl/_Feisty_Fawn/pidgin/2.1.1/](http://download.ubuntu.pl/_Feisty_Fawn/pidgin/2.1.1/)

the use the switchspell plugin ([http://plugins.guifications.org/trac/wiki/switchspell](http://plugins.guifications.org/trac/wiki/switchspell))

---

### Post by harce on 2007-11-15
if anybody runs into a way to save the choices for spellcheck like this buddy always english that one esperanto the other one german - i'll appreciate, cuz I cant find a solution for that...

---

### Post by por100pre1 on 2007-11-15
Be sure to have installed Aspell and the Aspell package for the language you want.

---

### Post by eks on 2008-07-08
If the Switch Spell plugin was before on the pidgin-plugin-pack, **why it was taken out**??

I just installed the plugin pack for Hardy (64 bits), but the installed files are only:

> 
/usr/lib/purple-2/autorejoin.so
/usr/lib/purple-2/autoreply.so
/usr/lib/purple-2/bash.so
/usr/lib/purple-2/dice.so
/usr/lib/purple-2/eight_ball.so
/usr/lib/purple-2/flip.so
/usr/lib/purple-2/highlight.so
/usr/lib/purple-2/ignore.so
/usr/lib/purple-2/irc-more.so
/usr/lib/purple-2/irchelper.so
/usr/lib/purple-2/listhandler.so
/usr/lib/purple-2/oldlogger.so
/usr/lib/purple-2/showoffline.so
/usr/lib/purple-2/simfix.so
/usr/lib/purple-2/slashexec.so
/usr/lib/purple-2/sslinfo.so
/usr/lib/pidgin/album.so
/usr/lib/pidgin/blistops.so
/usr/lib/pidgin/difftopic.so
/usr/lib/pidgin/gRIM.so
/usr/lib/pidgin/hideconv.so
/usr/lib/pidgin/irssi.so
/usr/lib/pidgin/lastseen.so
/usr/lib/pidgin/mystatusbox.so
/usr/lib/pidgin/nicksaid.so
/usr/lib/pidgin/plonkers.so
/usr/lib/pidgin/pidgin-schedule.so
/usr/lib/pidgin/sepandtab.so
/usr/lib/pidgin/xchat-chats.so


Also a usefull link from launchpad:

[https://answers.launchpad.net/ubuntu/+source/pidgin/+question/34803](https://answers.launchpad.net/ubuntu/+source/pidgin/+question/34803)

I found the all the sources here: [http://plugins.guifications.org/trac/downloads](http://plugins.guifications.org/trac/downloads)

But how do I compile them? Should I uninstall the package installed with Synaptic first?

And what's the difference between the Guifications and the PluginPack packages?


eks
Edit: this plug-in is **very very very** useful and is the one that fits the most on the international mentality of Ubuntu.

---

### Post by eks on 2008-07-10
Turned that question in launchpad into a bug at:

[https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/246905](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/246905)



eks

---

### Post by i_can_fly on 2008-07-13
Hello!
If you just need to have spell check in your language in pidgin and don't need to be able to choose a lang for every contact, you can get the job done very easily:

In a terminal type:
```
aspell dicts
```
That is to determine what dictionaries you have installed.(if there isn't one suited for your language, install the corresponding language pack from synaptic)
On my system the output is:
```
$ aspell dicts
bg
bg-w_english
bg-wo_english
en
en-variant_0
en-variant_1
en-variant_2
en-w_accents
en-wo_accents
en_CA
en_CA-w_accents
en_CA-wo_accents
en_GB
en_GB-ise
en_GB-ise-w_accents
en_GB-ise-wo_accents
en_GB-ize
en_GB-ize-w_accents
en_GB-ize-wo_accents
en_GB-w_accents
en_GB-wo_accents
en_US
en_US-w_accents
en_US-wo_accents
```

Create the file **.aspell.conf** in your home dir and put a line in it begining with the word **master** and then the name of the dictionary you want to use.

Mine looks like that:
```
$ more .aspell.conf
master bg-w_english
```

That's it. Restart pidgin and it should be working :)

---

