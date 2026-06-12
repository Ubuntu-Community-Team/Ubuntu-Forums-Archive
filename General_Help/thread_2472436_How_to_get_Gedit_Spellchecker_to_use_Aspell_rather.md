---
title: "How to get Gedit Spellchecker to use Aspell rather than Hunspell or other spellcheckr"
date: 2022-02-26
forum: General Help
---

### Post by swarup on 2022-02-26
I am using Ubuntu 18.04.6 LTS, and have used the Aspell spellchecker in Gedit for many years for spellchecking in the Bengali language, and have developed a large wordlist for the spellchecker which is specialized for my area of work, hence the need for the Aspell spellchecker. I shifted over to a new computer, and the problem is I think that Ubuntu has moved on to a different default spellchecker, perhaps Hunspell.

When in Gedit I go to tools => set language, there are three different Bengali language spellchecker options listed: (1) Bengali, (2) Bangali (Bangladesh), and (3) Bengali (India). But none of these three options make use of the bn.cwl word list contained in the aspell6-bn-0.02 folder. They may perhaps be using the Hunspell word list or some other word list. But not the Aspell word list. 

I have installed the Aspell spellchecker using the usual terminal commands which I've been using for many years, but when I activate the spellchecker, it is not using the word list which I have in the Aspell folder.

---

### Post by MAFoElffen on 2022-02-27
When I check the Gnome website docs for gedit, I still see ASpell: [https://help.gnome.org/users/gedit/stable/gedit-spellcheck.html.en](https://help.gnome.org/users/gedit/stable/gedit-spellcheck.html.en)
> 
 **Dictionaries**


  gedit uses     [Enchant]("http://www.abisource.com/projects/enchant/"),     a small system utility, for spell checking. Enchant can use     several different dictionaries to check your spelling. Two such     dictionary back-ends are Hunspell and Aspell.

 If the language you want to use is not available in gedit,     use your computer's software installer or package manager to install the     dictionary back-end that you want.
And from the AbiWord /Enchant Github:
> 
Enchant currently works with the following spell-checkers:

    * Hunspell (formerly Myspell)
    * Nuspell
    * GNU Aspell
    * Hspell
    * Voikko
    * Apple Spell (macOS only)
    * Zemberek
'aspell-bn is there in the Repo's and here is the complete changelog for the latest version:
```

aspell-bn (1:0.01.1-1-3) unstable; urgency=medium

  * Team upload.

  [Kartik Mistry]
  * debian/control:
    + Fixed VCS-* URLs.
    + Updated Standards-Version to 3.9.4
    + Bump debhelper compat to 9.
  * Applied wrap-and-sort for debian/control, debian/install files.
  * Updated debian/copyright.

  [ Vasudev Kamath ]
  * Make aspell-bn reproducible.
  * Declare compliance with Debian policy 3.9.7
  * Use secure URL for Vcs-* fields.

 -- Kartik Mistry <kartik@debian.org>  Sun, 13 Mar 2016 14:00:27 +0530

aspell-bn (1:0.01.1-1-2) unstable; urgency=low

  [Kartik Mistry]
  * Team upload.
  * debian/control:
    + Moved to Git. Updated Vcs-* fields.
  * debian/copyright:
    + Updated as per DEP-5 format.

 -- Debian-IN Team <debian-in-workers@lists.alioth.debian.org>  Thu, 02 Feb 2012 10:23:52 +0530

aspell-bn (1:0.01.1-1-1) unstable; urgency=low

  [Kartik Mistry]
  * Synce to upstream version. Added epoch as upstream version is lower than
    version we've in Debian.
  * debian/control:
    + Updated Standards-Version to 3.9.2
    + Added Build-Depends to aspell
    + Removed Build-Depends on cdbs
  * debian/copyright:
    + Updated for latest DEP-5 specification
  * debian/rules:
    + Updated to use dh

 -- Debian-IN Team <debian-in-workers@lists.alioth.debian.org>  Sat, 04 Jun 2011 10:47:45 +0530

aspell-bn (0.60.0.01.1.1-9) unstable; urgency=low

  [Kartik Mistry]
  * debian/control:
    + Updated Standards-Version to 3.8.4
    + Wrapped up Build-Depends and Uploaders
  * debian/copyright:
    + Updated as per DEP-5 specifications
    + Don't point to versionless symlink of license text
  * Updated package to use source format 3.0 (quilt)

 -- Debian-IN Team <debian-in-workers@lists.alioth.debian.org>  Fri, 07 May 2010 14:55:41 +0530

aspell-bn (0.60.0.01.1.1-8) unstable; urgency=low

  [Kartik Mistry]
  * debian/control:
    + [Lintian] Added ${misc:Depends} for debhelper dependency
    + Updated Standards-Version to 3.8.2
    + [Lintian] Updated extented description
  * debian/copyright:
    + Updated to use correct copyright symbol ©

 -- Debian-IN Team <debian-in-workers@lists.alioth.debian.org>  Mon, 22 Jun 2009 11:03:50 +0530

aspell-bn (0.60.0.01.1.1-7) unstable; urgency=low

  [Kartik Mistry]
  * Added debian/watch file
  * debian/copyright:
    + Moved copyright out of license section
    + Updated link of GPL
    + Added copyright year
  * debian/control:
    + Updated standards-version to 3.7.3
    + Use Homepage as control field
    + Updated package descriptions
    + Added VCS-* fields
  * debian/changelog:
    + Fixed typo from previous changelog entry

 -- Debian-IN Team <debian-in-workers@lists.alioth.debian.org>  Sat, 26 Jan 2008 14:23:18 +0530

aspell-bn (0.60.0.01.1.1-6) unstable; urgency=low

  [Kartik Mistry]
  * Set maintainer address to Debian-IN Team
  * Updated standards-version to 3.7.2
  * Updated debhelper compatibility to 5
  * debian/copyright: updated according to standard copyright
  * debian/control: fixed build-dependency, added homepage to long description
  * debian/README.Debian: updated according to standard file

 -- Debian-IN Team <debian-in-workers@lists.alioth.debian.org>  Mon, 21 May 2007 10:30:01 +0530

aspell-bn (0.60.0.01.1.1-5) unstable; urgency=low

  * Added a line 'set -e; \' just before the for loop in debian/rules
  * Added the u-beng.cset and u-beng.cmap files to debian/install to install
    the two files in the package (Closes: #327788)

 -- Soumyadip Modak <soumyadip@softhome.net>  Wed, 21 Sep 2005 13:40:00 +0530

aspell-bn (0.60.0.01.1.1-4) unstable; urgency=low

  * Added the aspell-bn.info-aspell file. Missed it last time.

 -- Soumyadip Modak <soumyadip@softhome.net>  Sun, 04 Sep 2005 11:22:00 +0530

aspell-bn (0.60.0.01.1.1-3) unstable; urgency=low

  * Changed control (it's now identical to the aspell-en control). 
  * Removed prerm, preinst and postinst.
  * Added a couple of new files (install and dirs) to mirror the debian
    directory structure of aspell-en
  * aspell-bn should conform to the new aspell dictionary packaging policy
    (Closes: #319681)

 -- Soumyadip Modak <soumyadip@softhome.net>  Sun, 04 Sep 2005 11:16:00 +0530

aspell-bn (0.60.0.01.1.1-2) unstable; urgency=high

  * Sorry, I messed up the last upload.  Trying again.
  * New version which works with aspell 0.60.  (Closes: #297149)
    Thanks to Ognyan Kulev for his help with this bug.
  * Uploaded for Soumyadip by Jaldhar H. Vyas <jaldhar@debian.org>

 -- Jaldhar H. Vyas <jaldhar@debian.org>  Mon, 28 Mar 2005 09:37:17 -0500

aspell-bn (0.60.0.01.1.1-1) unstable; urgency=high

  * Failed  upload.

 -- Jaldhar H. Vyas <jaldhar@debian.org>  Sun, 27 Mar 2005 16:29:54 -0500

aspell-bn (0.50.1-4) unstable; urgency=low

  * reuploaded to fix botched upload. 
  * Uploaded for Soumyadip by Jaldhar H. Vyas <jaldhar@debian.org>

 -- Jaldhar H. Vyas <jaldhar@debian.org>  Fri, 30 Apr 2004 01:16:08 -0400

aspell-bn (0.50.1-3) unstable; urgency=low

  * Repacked the source so the package is no longer debian-native.
  * Removed unneeded code from debian/rules
  * removed debian/dirs as it is unused.
  * Fixed so that configure is called with the right options.
  * Uploaded for Soumyadip by Jaldhar H. Vyas <jaldhar@debian.org>

 -- Jaldhar H. Vyas <jaldhar@debian.org>  Thu, 29 Apr 2004 23:32:00 -0400

aspell-bn (0.50.1-2) unstable; urgency=low
  
  * Corrections to the control file to ensure that aspell is listed among 
    dependencies.

 -- Soumyadip Modak <soumyadip@softhome.net>  Mon, 22 Mar 2004 22:46:21 +0530

aspell-bn (0.50.1-1) unstable; urgency=low

  * Initial Release.

 -- Soumyadip Modak <soumyadip@softhome.net>  Sun, 21 Mar 2004 00:15:33 +0530

```
There are no recent changes for years. It has been stable for years.

---

### Post by swarup on 2022-02-27
Thank you for taking interest in my question. My problem is that despite having installed Aspell, Gedit is not using it as the spellchecker. Words that are in my wordlist and hence should not be getting underlined in red, are underlined in red. And words that are not in my wordlist and hence should be getting underlined in red, are not getting underlined. So when, in Gedit, I open "tools" and enable the spellchecker, it is using a different spellcheck than the one I installed. So what I need guidance for is how to make Gedit use Aspell. Yes, I have aspell-bn and have installed it for use with Gedit. But Gedit is not using it.

---

### Post by Holger_Gehrke on 2022-02-28
gedit uses enchant to do spellchecking. enchant is a wrapper that makes all spellcheckers work the same as far as a program using enchant is concerned. To configure enchant there are two files: /usr/share/enchant/enchant.ordering (system wide) and ~/.config/enchant/enchant.ordering (personal). Each line in enchant.ordering has the form {language code}:program[,program ...] so it should be 'bn:aspell,ispell,myspell' for Bengali if you want to give aspell the highest priority. 

If this doesn't give you access to your personal wordlist, you might want to have a look at the instruction in the readme for libenchant at [https://github.com/AbiWord/enchant](https://github.com/AbiWord/enchant) which explains how to setup personal word lists for enchant which will be shared with all supported spell checkers.

Holger

---

### Post by swarup on 2022-02-28
Hi Holger,
Your post was greatly educational for me. By reading it as well as the resources you provided, I could get a sense as to what it is that enchant does. So enchant is the manager of the spellcheck apparatus, and it can employ various spellchecker dictionary lists, together, for use in clients such as Gedit.

Now there are three files which I have identified as critical to my success in getting Gedit/enchant to include my aspell Bengali word list in its spellchecker:
1) The aspell bn wordlist: ~/aspell6-bn-0.02/bn.cwl. This is my word list, which I wish to use. It contains 439,000 words and can be uncompressed to access the word list as bn.wl, using the following commands in a terminal window:
```
&#65279;cd ~/aspell6-bn-0.02
&#65279;preunzip bn.cwl
```
2) The personal enchant wordlist: ~/.config/enchant/bn.dic. This list contains 15,000 words.
3) The enchant.ordering (system wide) file to which you referred: /usr/share/enchant/enchant.ordering

My computer does not seem to have the file ~/.config/enchant/enchant.ordering (personal) to which you referred.

Currently I see three possible options for getting my bn.cwl word list to be used by Gedit:
1. Uncompress and copy-paste my entire 439,000 word list bn.wl and paste the list into the 2nd file mentioned above, the personal enchant bn.dic wordlist. I do not know how well the personal enchant dictionary would tolerate an addition of 439,000 words? This would be an easy solution if such a large addition is tolerated by the enchant personal Bengali dictionary.
2. I read the readme for libenchant to which you refer in your post. There it talks about how to "share word lists with Enchant". And it says to achieve this, one is to "merge it with the corresponding Enchant file". Here are the instructions for how to do it:
> Use the following command, replacing ENCHANT-DICT
and OTHER-DICT with the corresponding dictionary file names:

cat ENCHANT-DICT OTHER-DICT | sort -u > merged.txt

Take a look at merged.txt to check the merge has worked, then

mv merged.txt ENCHANT-DICT
rm OTHER-DICT
ln -s OTHER-DICT ENCHANT-DICT
3. The enchant.ordering (system wide) file to which you refer, if I simply add the line 'bn:aspell,ispell,myspell', would that make enchant include my bn.cwl word list file in its spell checking in Gedit?

So above are the three options which I see. The first option is easiest for me, if it would work. Have I understood correctly the three options?

---

### Post by Holger_Gehrke on 2022-02-28
The personal configuration file has the same structure as the system wide one. You can just copy /usr/share/enchant/enchant.ordering to ~/.config/enchant/enchant.ordering and add the line for Bengali to that copy. Personal configuration overrides system configuration. If aspell is correctly configured to use your ~/aspell6-bn-0.02/bn.cwl, then this would be the least invasive method of getting things to work. If that doesn't work, check whether aspell actually "knows" about your dictionary with 'aspell dicts'. If that doesn't show some dictionaries whose name starts with bn, you've got a problem with aspell not with enchant. With the non-standard location of the .cwl file I assume that that's what is actually going on.

Holger

---

### Post by swarup on 2022-02-28
Good news! Doing what you have said to do here in your last post (post #6) has created the needed link. It is working now! Really great, I can't believe it -- thank you so much.

I shall continue to do further testing in the coming days. But as of now I shall declare that this problem is solved.

---

### Post by MAFoElffen on 2022-03-01
If solved, please remember to got to the upper right of the first page of your thread,  to use the "Thread Tools" link to mark your thread as "Solved". That way others may find your solution to their own similar problems.

---

