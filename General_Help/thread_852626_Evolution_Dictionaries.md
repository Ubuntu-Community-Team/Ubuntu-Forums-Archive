---
title: "Evolution Dictionaries"
date: 2008-07-07
forum: General Help
---

### Post by acabre on 2008-07-07
Hello All,

I'm using Evolution 2.22.2 and can't seem to get any dictionaries installed. From what I've read, Evo uses the aspell dictionaries (although many users have said that installing gnome-spell solves this problem). I believe I have the proper dictionaries installed (see below), but Evo shows no dictionaries, and doesn't spell check.

```

paul@tamlin:~$ apt-show-versions -a aspell
aspell	0.60.5-1ubuntu2	install ok installed
aspell	0.60.5-1ubuntu2	hardy
aspell/hardy uptodate 0.60.5-1ubuntu2
paul@tamlin:~$ apt-show-versions -a aspell-en
aspell-en	6.0-0-5.1	install ok installed
aspell-en	6.0-0-5.1	hardy
aspell-en/hardy uptodate 6.0-0-5.1
paul@tamlin:~$ apt-show-versions -a gnome-spell
gnome-spell	1.0.7-1ubuntu2	install ok installed
gnome-spell	1.0.7-1ubuntu2	hardy
gnome-spell/hardy uptodate 1.0.7-1ubuntu2


```

---

### Post by sdennie on 2008-07-07
When you are composing an e-mail, have you gone to Edit->Current Languages and selected the languages you want to include?  I do this for Spanish/English (after having both aspell dictionaries installed) and it seems to work fine.

---

### Post by acabre on 2008-07-07
> **vor said:**
> When you are composing an e-mail, have you gone to Edit->Current Languages and selected the languages you want to include?  I do this for Spanish/English (after having both aspell dictionaries installed) and it seems to work fine.

When composing, I don't have an "Current Languages" option under Edit or any other menu. However, I imagine that the languages shown in Edit->Preferences->Composer Preferences->Spell Checking would be the same ones you could select. My list under this section is empty.

---

### Post by sdennie on 2008-07-07
Strange.  Maybe going to System->Administration->Language Support and then restarting Evolution will fix the problem.

---

### Post by acabre on 2008-07-07
> **vor said:**
> Strange.  Maybe going to System->Administration->Language Support and then restarting Evolution will fix the problem.

Language Support notified me that I was missing the "language-pack-kde-en" and "language-pack-kde-en-base" packages. However, installing them didn't change Evolution's dictionaries or spell check support. Language Support shows I am setup for English.

---

### Post by pjasper on 2008-07-11
I have the same problem (although I think Evolution's spell checking was working about a year ago when I was running Feisty Fawn - I'm now on Hardy Heron via upgrades). The English dictionaries don't show up in the Edit->Preferences->Composer Preferences->Spell Checking list, although I can install other language packs (e.g., aspell-es) and they do show up. 

I've checked my aspell and gnome-spell settings and they're the latest and greatest (same as those listed at the top of this thread).

I've tried everything recommended here:

[http://www.go-evolution.org/FAQ#Why_does_Spellchecking_not_work.3F](http://www.go-evolution.org/FAQ#Why_does_Spellchecking_not_work.3F)

but to no avail.

If anyone's had any success in fixing this, I'd like to hear about it. Unfortunately, one of the mail systems I have to connect to is a Microsoft Exchange server, so Evolution seems the only way to go on Linux.

Paul

---

### Post by dcstar on 2008-07-12
> **pjasper said:**
> I have the same problem (although I think Evolution's spell checking was working about a year ago when I was running Feisty Fawn - I'm now on Hardy Heron via upgrades). The English dictionaries don't show up in the Edit->Preferences->Composer Preferences->Spell Checking list, although I can install other language packs (e.g., aspell-es) and they do show up. 
.......

I can only suggest you completely remove the aspell-en package, and then do a manual search and delete of any files associated with the package before re-installing. Something in the upgrade process may have not worked.

Also create a new user account and see how Evolution behaves with that fresh profile.

---

### Post by acabre on 2008-07-14
Building on dcstar's advice, I completely removed and reinstalled the following packages:
```

aspell 
aspell-en 
gnome-spell 
language-support-en 
language-support-translations-en 
language-support-writing-en 
thunderbird-locale-en-gb 
ubuntu-desktop  
ispell 
iamerican 
ibritish  
myspell-en-gb 
myspell-en-us  

```

I reinstalled libaspell15 since completely removing it was too painful.

I still had no dictionaries.

I then created a new user, and set up Evo. In this user I have dictionaries in Evo, and it spell checks! I'll have to look and see if I can get my established profile to shape up tomorrow!

---

### Post by acabre on 2008-08-28
Sorry for the long lapse. Hope somebody's still interested in this problem.

Here's a comprehensive update:

Back in July, I verified that new accounts have the correct dictionaries installed in Evolution. However, this isn't really helpful since recreating my account isn't really an option to enable spellcheck in Evolution.

At this point, the problem appears to be that no dictionaries appear under the Preferences>>Compose Preferences>>Spell Checking pane.

I attempted to get Evo into a state similar to a new account by completely removing (through apt-get and Synaptic, I've done this multiple times) evolution, evolution-common, evolution-exchange, evolution-plugins and openoffice.org-evolution. evolution-data-server is required by several gnome apps, so it was only reinstalled. I also deleted the ~/.evolution folder. This didn't resolve the problem.

I then created a new account, copied the pristine directory, installed evolution, and then diffed the folders. This showed some new folders created. I then uninstalled as above, deleted ~/.evolution and additionally removed ~/.gconf/apps/evolution and ~/.gconf/apps/gnome-dictionary folders. After reinstalling, this didn't resolve the issue.

I then again followed the directions linked above by pjasper ([http://www.go-evolution.org/FAQ#Why_does_Spellchecking_not_work.3F]("http://www.go-evolution.org/FAQ#Why_does_Spellchecking_not_work.3F")). gconf-editor, under GNOME/Spell, showed language=0, as well as a language0=38, language1=39, language2=40. I created the languages=en-US key as recommended in the linked document, but this didn't fix the problem. I then thought that the resource might have a typo, so I deleted language and created a string with the same keyname ( ie language=en-US). This didn't work, so I followed the instructions to remove the entire Spell config. Upon rebooting and relaunching Evolution, Spell has been recreated with the following entries:

```

known_languages=202
languages=0
mtime=0

```

I then re-followed the FAQ instructions about setting alternatively language and languages to a "space-separated list of the languages you have enabled (i.e. en-US es for US english and Spanish)." I still have no dictionaries in Evolution.

At this point, I am at a loss as to what to try to troubleshoot next. Any help will be greatly appreciated.

--- Edit ---

Writing this post gave me the idea of diffing the working and unworking ~/.gconf/GNOME/Spell/%gconf.xml. It appears to me that the site linked above is wrong. The working gconf.xml is as follows:

```

<?xml version="1.0"?>
<gconf>
        <entry name="known_languages" mtime="1219942625" type="int" value="202">
        </entry>
        <entry name="mtime" mtime="1219942625" type="int" value="0">
        </entry>
        <entry name="language0" mtime="1219942625" type="int" value="38">
        </entry>
        <entry name="language1" mtime="1219942625" type="int" value="39">
        </entry>
        <entry name="language2" mtime="1219942625" type="int" value="40">
        </entry>
        <entry name="languages" mtime="1219942625" type="int" value="3">
        </entry>
</gconf>

```

It looks like "languages" is supposed to contain the number of dictionaries installed (the working Evo shows 3) and an integer languageX describing them. When I set these keys in my account, starting Evolution overrides the languages key and sets it to 0.

I tried removing write permissions to the key, but even though it remains 3 Evo still shows no dictionaries.

---

### Post by acabre on 2008-11-05
For the record, none of the above techniques solved this problem.

However, upgrading to 8.10 has.

---

### Post by wmatthews on 2009-02-24
The only thing that needs to be installed is gnome-spell and restart Evolution.  That worked just fine for me.

---

### Post by pjasper on 2009-02-24
> **wmatthews said:**
> The only thing that needs to be installed is gnome-spell and restart Evolution.  That worked just fine for me.
Believe me, I tried that and a whole bunch of other things. Eventually, one of the Ubuntu upgrades to Evolution fixed the dictionary problems, although Evolution would still crash quite regularly for other reasons.

My client recently upgraded their Exchange server to Exchange 2007, so I'm currently running Outlook 2003 under Crossover. Once Ubuntu supports the new version of Evolution that has MAPI support, I'll give that a try. But for the moment I'm not missing Evolution.

---

