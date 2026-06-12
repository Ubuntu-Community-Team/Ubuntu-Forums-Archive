---
title: "Help Me Once &amp; For All: Openoffice Spellcheck Never Works."
date: 2006-10-19
forum: General Help
---

### Post by efrancolaporte on 2006-10-19
It's the 3rd time I create a thread about this.

Nobody EVER responds to them, WTF.  I'm so tired of this.:mad: 

WHY does OpenOffice's spellcheck DOES NOT WORK???????]](*,) 

Yes, I DID RTFM. (Read The ******* Manual)
Yes, I DID set my language as english.
Yes, I DID enable it in the options.
Yes, I DID install all the language packs you could ever think of.
Yes, I DID make sure there is that blue checkmark before the language in OpenOffice's options.

And the spellcheck NEVER works when I create new documents.:evil: 

However, the spellcheck DOES WORK IN ABIWORD. So WHY NOT OpenOffice????

You know what's even more ridiculous? If I open my Microsoft Office .doc documents that I created in Windows, the spellcheck DOES work.

But as soon as I create a new document from OpenOffice, spellcheck NEVER WORKS.

It ALWAYS says there are no found mistakes.


I TRIED googling for help. I CAN'T FIND ANY.

Can I finally get some help please, so that I don't have to bump my old threads every freakin day always seing them empty???? Aargh.

---

### Post by drpaul on 2006-10-19
That does sound very strange. What exactly does happen when you try to do a spell check in OpenOffice?

Paul

---

### Post by matthew on 2006-10-19
> **efrancolaporte said:**
> It's the 3rd time I create a thread about this.

Nobody EVER responds to them, WTF.  I'm so tired of this.:mad: 

Can I finally get some help please, so that I don't have to bump my old threads every freakin day always seing them empty???? Aargh.I'm going to sympathetically and kindly suggest that your thread isn't being answered simply because no one else seems to be experiencing this problem...at least that seems the most likely explanation. See the "unanswered thread?" link in my signature for more details.

---

### Post by HereInOz on 2006-10-19
I seem to have the same problem.  I don't use spellcheck much, so I have never noticed it, but after seeing your post, I checked it out and indeed, I create a document in Open Office, and spellcheck it, and I am told that the spellcheck is complete with no errors, but there are clearly errors in the document.

I can't solve it either at the moment.  I guess this doesn't help, but it may make you feel less alone in the world.

---

### Post by finalbeta on 2006-10-19
I don't know what version you are on, but in edgy, it's openofice 2.0, spellchecking is much better in this version. Perhaps that helps you.

---

### Post by efrancolaporte on 2006-10-19
> **HereInOz said:**
> I seem to have the same problem.  I don't use spellcheck much, so I have never noticed it, but after seeing your post, I checked it out and indeed, I create a document in Open Office, and spellcheck it, and I am told that the spellcheck is complete with no errors, but there are clearly errors in the document.

I can't solve it either at the moment.  I guess this doesn't help, but it may make you feel less alone in the world.

Yes, It does make me feel less alone.  O:) thank you.

Yeah I use OpenOffice.org 2.0
What happens when I do a spellcheck with errors is that it simply states there are no errors, like if I was doing so on a blank page.

Anyway I tried re-installing OpenOffice 2.0, but it didn't change a thing.

---

### Post by holepunch on 2006-10-19
I've had the same problem.  When I go into the language options it tells me the language is set to Australian English.  If I set it to English UK it then picks up my spelling errors.  

However it only seems to solve the problem temporarily because it defaults back to Australian English after a reboot and new page is started.

---

### Post by drpaul on 2006-10-20
If you look at Tools:Options:Language Settings

do you have Hunspell spell checker & New Thesaurus modules?

what dictionaries do you have?

Paul

---

### Post by elfgoh on 2006-10-21
Try this thread:

[http://www.oooforum.org/forum/viewtopic.phtml?t=32691&highlight=spellchecker+set+language](http://www.oooforum.org/forum/viewtopic.phtml?t=32691&highlight=spellchecker+set+language)

Anyway, I must say that the solution is pretty counter
intuitive. In a nutshell, what you need to do is to

- Press F11 to bring up the styles and formatting
menu.
- Right click on "Default" and click "modify".
- Click on the fonts tab and select the language you
want your dictionary to be.

However, this is a temporary solution. To have a
permanent solution. You need to

- Create a blank document.
- Set the language to "English (UK)" under Tools ->
Options -> Language Settings -> Languages.
- Set the Default paragraph style as outlined above,
if it is not already so set.
- Check the character styles in the Style list under
the A icon in the Style list,
- Do File -> Templates -> Save, giving it suitable
name for your normal template, such as Default-Writer.

- Next go to File -> Templates -> Organize, find your
template under "My Templates", select it, right-click,
and choose "Set As Default Template". All new
documents will now be created from that template
with any style settings you have saved to it,
including language settings.

Of course documents not created by yourself may have
different language
attributes assigned to text or documents you have
previously created by
have other language attributes assigned to some or all
of the text.

HTH.

---

### Post by efrancolaporte on 2006-10-21
Allright everybody, read this.
Although my problem isn't completely resolved, it slightly improves the situation.

I openned a Microsoft Office document that ALREADY has spellcheck enabled, FROM Microsoft Windows, where as I said in my 1st post, the spellcheck still works in Open Office, and I emptied it, cleared all its contents and saved it as the new default template. (Why didn't I think of this sooner?)

Now every new document I create starts with the spellcheck enabled in the language of the template I saved.:) 

Here's why I'm still not satisfied though:
My default template has its spellcheck language set to "French (Canada)" and it's great because it's my 1st language and it does correct the errors in french.

However, if I type something in english such as:
"Hello, how do you do?"
it shows up as mistakes. Okay, now if I run the spellcheck and select language: "English (UK)", it doesn't have any suggestion for the "mispelled" world such as "Hello" and I am forced to click Ignore, and then it notes the 2nd word, "how" as a mistake again and the language of the spellcheck is again reverted to French (Canada).

So it literally can't spellcheck in a language other than my default template.

Another interesting note, while I was running this template with the french spellcheck enabled, I tried going in OpenOffice's options again and went to "Writting Aids" ... even though it checks for french spelling, the language in the options is STILL set to "English (UK)". And if I click the button "Edit" and change it to french or any other language, and click close, I saw that it brought it back to English (UK) as soon as I try to edit it again to see if it's still set to what I set it last. (it wasn't!)

So.... it can't spellcheck shit unless I set the spellcheck in a document from Windows. nice. :-k 

I also tried Elfgoh's method of using F11 to change the Styles & Formating and the language under "Font" but it doesn't change anything in practice when I do it.

---

### Post by wimva on 2006-10-22
Elfgoh, your tip on using F11 does work for me.
Thanks. very much.

---

### Post by Smooth Criminal on 2006-10-27
[SIZE="2"][FONT="Verdana"]I experienced the same problem too.

For me the cause was that OpenOffice only had a spellcheck dictionary for English (USA), but since I live in Canada my profile was set to English (Canada) (It is under System > Administration > Language Support).

Go in there and see what your language profile is set to. Mine was set to English (Canada), but once I changed it to English (USA), the spell check in OpenOffice worked fine!

Make sure you close and reopen OpenOffice if you make any changes in language support. Also, this change will affect new documents. Any previous documents will have to be changed over manually as mentioned above. Just use the temporary solution posted above. Hope this helps.[/FONT][/SIZE]

---

### Post by curlyboy on 2006-10-31
As mentioned the problem is related to the fact that there is no dictionary installed for the language selected under the 'Tools-->Options-->Language Settings-->Languages-->Default Languages for documents' setting in openoffice.  You can tell if a dictionary is installed if there is a checkmarked 'abc' icon next to the language name. 

To get things working you need to install the dictionary for the language.

Browse on over to [ http://wiki.services.openoffice.org/wiki/Dictionaries]("http://wiki.services.openoffice.org/wiki/Dictionaries") and follow the instructions there.  (I started up openoffice as the root user and used the dictionary installer in 'administrator' mode, this way the dictionary was installed for all users.)

---

### Post by Brianm on 2006-11-08
Further to "efrancolaporte:"

Had same problem with OpenOffice under Windows XP.  Installed OpenOffice at work, and everything is tickety-boo.

Installed at home, and Spellcheck does not work at all on "AutoSpellcheck," and when "Spellcheck" invoked, it informs me there were no spelling errors.  Also, that same message box has its "Dictionary Language" box blank.

Thinking I had installed wrongly; downloaded install package from work PC #1, to my Sony digicam, whence it was uploaded to work PC #2.  Perfect install.  Everything is tickety-boo.

Installed from digicam to home machine, and again - no Spellcheck!  Repeated installation several times, carefully deinstalling and erasing each time.  Still no Spellcheck.

Work PC are MS Windows XP Pro.  Home PC is MS Windows XP Home, but it is also a cheapie, with amazingly poor performance.  Current suspects are: flakey hardware; malware; system differences.  Will be using both French and Cdn. English.  
Will inform you of final diagnosis.

---

### Post by mysteredom on 2006-11-29
Had the same problem, no spellcheck available.

Now it work fine

I made sure all of this was right to spellcheck my documents in French (Canada)

1. Tools-> Options-> Language -> Default language for documents :French (Canada)
2. Tools-> Options -> OpenOffice.org -> Paths -> Dictionnaries, User-Defined dictionnaries & Writing Aids all set to : [your path to OpenOffice.org 2.0]\share\dict\ooo
3. File -> Wizard -> Install new dictionnaries then follow the steps for your langage.
4. Reboot.
5. It should work now...  (check in Tools-> Options-> Language -> writing Aids -> Available language modules -> Edit , your langage should be there

If this procedure doesn't work, you can try the manual counterpart (still, do the first 2 steps):
3. Close OpenOffice
4. go to  [http://lingucomponent.openoffice.org/download_dictionary.html](http://lingucomponent.openoffice.org/download_dictionary.html)
and download the languages (dictionnary & thesaurus) of your choice, extracting the .zip files to [your path to OpenOffice.org 2.0]\share\dict\ooo
5. Open the ooo directory
6. Make sure you have those files there (for french Canada):
fr_FR.aff
fr_FR.dic
hyph_fr_FR.dic
th_fr_FR_v2.dat
th_fr_FR_v2.idx
7.There's the dictonary.lst file there. make a copy then open the original with notepad and add those lines:
DICT fr CA fr_FR
HYPH fr CA hyph_fr_FR
THES fr CA th_fr_FR_v2
(or follow this syntax to add other languages, as stated in the introduction of the text file)
8. Save close and reboot
9. It should work now...  (check in Tools-> Options-> Language -> writing Aids -> Available language modules -> Edit , your langage should be there

Hopes this solve it for good...

---

### Post by mysteredom on 2006-11-29
oops, did some windows walkthrough on a linux forum... :D 

read this for manual walkthrough on Linux:

[http://homepage.ntlworld.com/garryknight/linux/oodict.html](http://homepage.ntlworld.com/garryknight/linux/oodict.html)

---

### Post by silex on 2006-12-07
I was having the same problem as the original poster, and installing the hunspell package did the trick for me. :)

---

### Post by Richard J Moore on 2006-12-19
I have experienced similar problems with spellcheck over several releases. In my case autocheck detects mis-spellings but does not correct them. The problem relates to fonts.  If I select Nimbus Roman No 9 then spellcheck works absolutely fine. If I use Times or Times New Roman or Thorndale (and there may be others) then it doesn't work. 
The tip of using F11 doesn't seem to help in my case.

Somewhere way back there was an explanation of this problem on the ooo mailing list, but I've forgottent the details. If you find my alternative email address (rasman@uk.ibm.com) in the archive you might stumble upon the thread.

---

### Post by bodhi.zazen on 2006-12-19
sudo aptitude install abiword && sudo aptitude remove OOO :p

---

### Post by Hagar Delest on 2006-12-28
Hi all,

See here if that helps : [[Tuto] Spell check]("http://www.oooforum.org/forum/viewtopic.phtml?t=50862"). It is based on the message from the OOo mailing list but with additional information.

---

### Post by domer on 2007-02-08
<<< SIMPLE FIX >>>

Open/create an Openoffice document, Tools -> Options -> Expand "Language Settings" -> Double Click on "Language" -> Where is says "Default language for documents", there is a subsection "Western". Select UK English or USA English. Done!!!

I had Canada English and the spell check utility does not work for it.

---

