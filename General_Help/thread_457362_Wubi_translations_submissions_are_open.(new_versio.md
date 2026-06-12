---
title: "Wubi translations submissions are open.(new version)"
date: 2007-05-28
forum: General Help
---

### Post by ecology2007 on 2007-05-28
**EDIT by ago: Wubi translations are now done via rosetta, please use [https://translations.launchpad.net/wubi](https://translations.launchpad.net/wubi) and ignore the instructions below**












If you want to translate wubi in your language, your contribution is welcome.:D
It is easy to do and it should not take you more than 20 minutes.
Send me a private message if you are interested.

See below in the attached file and post your work as attachment here :

**Update October 7 th 2007.(Gusty)**
Please check this post.
[http://ubuntuforums.org/showpost.php?p=3387362&postcount=50](http://ubuntuforums.org/showpost.php?p=3387362&postcount=50)

--------------------------------------------
**Update June 9 th 2007.(Old version closed)**

New set of translations is available.
If you want you can use po files (Thanks Hampus) :
[http://ubuntuforums.org/showpost.php?p=2753348&postcount=9](http://ubuntuforums.org/showpost.php?p=2753348&postcount=9)

---

### Post by ecology2007 on 2007-05-28
=========================================================== 
**Wubi translations** :rev->189 
=========================================================== 
June 9 2007.
===========================================================
**New language :**
===========================================================
Open english.nsh in any text editor, and translate the strings between " ". 
Replace ${LANG_ENGLISH} by the value given in the table below. 
Save the file under the name given below. 
 
Use the same ponctuation, ie  
    use : when there is : 
    use . when there is . 
    use ... when there is ... 
    use (%d) when there is (%d)
    use (%s) when there is (%s)     
You must use $\r$\n when there is $\r$\n. This is the new line sign, which allows to make multiline translations. 
 
Ie : 
 
LangString InstallHeaderInitializing ${LANG_ENGLISH} "Initializing..." 
 
becomes in spanish, in the file spanish.nsh 
 
LangString InstallHeaderInitializing ${LANG_SPANISH} "Inicializando..." 

===========================================================
**Existing language :**
===========================================================
Check if the corresponding file in ./nsis does not have remaining english strings.
Same rules as above applies.

===========================================================
**Rosetta :**
===========================================================
Rosetta is not ready yet to accept our translations.
For now it only displays the current status of our translations.
Please do not edit your translations directly in Rosetta, 
as they may be overwritten.

=========================================================== 
**Translation submission **
=========================================================== 
You can can translate as many languages as you want, see the list of allready translated languages, and post the file here as attachment : 
Send us only the files you translated.
 
[http://ubuntuforums.org/showthread.php?t=457362](http://ubuntuforums.org/showthread.php?t=457362)

===========================================================
** List of valid languages files : languages codes :**
```

albanian.nsh        :    ${LANG_ALBANIAN}
arabic.nsh        :    ${LANG_ARABIC}
basque.nsh        :    ${LANG_BASQUE}
belarusian.nsh        :    ${LANG_BELARUSIAN}
bosnian.nsh        :    ${LANG_BOSNIAN}
breton.nsh        :    ${LANG_BRETON}
bulgarian.nsh        :    ${LANG_BULGARIAN}
catalan.nsh        :    ${LANG_CATALAN}
croatian.nsh        :    ${LANG_CROATIAN}
czech.nsh        :    ${LANG_CZECH}
danish.nsh        :    ${LANG_DANISH}
default.nsh        :    ${LANG_DEFAULT}
dutch.nsh        :    ${LANG_DUTCH}
english.nsh        :    ${LANG_ENGLISH}
estonian.nsh        :    ${LANG_ESTONIAN}
farsi.nsh        :    ${LANG_FARSI}
finnish.nsh        :    ${LANG_FINNISH}
french.nsh        :    ${LANG_FRENCH}
galician.nsh        :    ${LANG_GALICIAN}
german.nsh        :    ${LANG_GERMAN}
greek.nsh        :    ${LANG_GREEK}
hebrew.nsh        :    ${LANG_HEBREW}
hungarian.nsh        :    ${LANG_HUNGARIAN}
icelandic.nsh        :    ${LANG_ICELANDIC}
indonesian.nsh        :    ${LANG_INDONESIAN}
irish.nsh        :    ${LANG_IRISH}
italian.nsh        :    ${LANG_ITALIAN}
japanese.nsh        :    ${LANG_JAPANESE}
korean.nsh        :    ${LANG_KOREAN}
kurdish.nsh        :    ${LANG_KURDISH}
latvian.nsh        :    ${LANG_LATVIAN}
lithuanian.nsh        :    ${LANG_LITHUANIAN}
luxembourgish.nsh    :    ${LANG_LUXEMBOURGISH}
macedonian.nsh        :    ${LANG_MACEDONIAN}
malay.nsh        :    ${LANG_MALAY}
mongolian.nsh        :    ${LANG_MONGOLIAN}
norwegian.nsh        :    ${LANG_NORWEGIAN}
norwegiannynor.nsh    :    ${LANG_NORWEGIANNYNOR}
polish.nsh        :    ${LANG_POLISH}
portuguese.nsh        :    ${LANG_PORTUGUESE}
portuguesebr.nsh    :    ${LANG_PORTUGUESEBR}
romanian.nsh        :    ${LANG_ROMANIAN}
russian.nsh        :    ${LANG_RUSSIAN}
serbian.nsh        :    ${LANG_SERBIAN}
serbianlatin.nsh    :    ${LANG_SERBIANLATIN}
simpchinese.nsh        :    ${LANG_SIMPCHINESE}
slovak.nsh        :    ${LANG_SLOVAK}
slovenian.nsh        :    ${LANG_SLOVENIAN}
spanish.nsh        :    ${LANG_SPANISH}
swedish.nsh        :    ${LANG_SWEDISH}
thai.nsh        :    ${LANG_THAI}
tradchinese.nsh        :    ${LANG_TRADCHINESE}
turkish.nsh        :    ${LANG_TURKISH}
ukrainian.nsh        :    ${LANG_UKRAINIAN}
uzbek.nsh        :    ${LANG_UZBEK}
valencian.nsh        :    ${LANG_VALENCIAN}
welsh.nsh        :    ${LANG_WELSH}
```

---

### Post by ecology2007 on 2007-05-28
Already assigned :

> 
Albanian :
Arabic :
Basque :
Belarusian :
Bosnian :
Breton :
Bulgarian :
Catalan :
Croatian :
Czech :
Danish :
Default :
** Dutch : rmzelle**
English :
Estonian :
Farsi :
Finnish :
** French : Kynax**
Galician :
**German : miketowninc**
** Greek : madmetal/Spyros**
Hebrew :
** Hungarian :  JegHegy**
Icelandic : 
Indonesian :
Irish :
** Italian : Darkmaster**
** Japanese : Nazo**
Korean :
Kurdish :
Latvian :
** Lithuanian : Joshas**
Luxembourgish :
Macedonian :
Malay :
Mongolian :
Norwegian :
NorwegianNynor :
Polish :
** Portuguese : Jordao**
** PortugueseBR : fabioGramos**
Romanian :
Russian :
Serbian :
SerbianLatin :
** SimpChinese : [zjtopspeed gmail.com]("http://ubuntuforums.org/member.php?u=309692")**
Slovak :
Slovenian :
**Spanish : open2linux**
** Swedish : Hampus**
Thai :
** TradChinese : Swellwin**
Turkish :
Ukrainian :
Uzbek :
Valencian :
Welsh :===========================================================
[B][COLOR=Black] NSIS 2.28 translations. 
June 10 2007.[/COLOR][/B]
===========================================================
If your language[COLOR=Red] is not in this list[/COLOR], you will have to translate NSIS language files first.
All the required and current NSIS files are in the attachment below.
>  ===========================================================
** First Step**
===========================================================
Use MakeLangId.exe to find out what is your lang id.

Ie for URDU (pakistan) : 
LANG_URDU
SUBLANG_URDU_PAKISTAN
lang id will be 1056
The name of your translated files will be the one of sublang without _.

Filename of nlf file for basic NSIS will be urdupakistan.nlf
Filename of nsh file for modernUI will be urdupakistan.nsh

===========================================================
** Second Step**
===========================================================
Open Language files\english.nlf in any text editor.
Replace the lang id with the one you have just made.
    
    Do not translate the lines starting by #
    Do not translate the text $(^...)
    Use \r when you see \r.

If your language is right to left, look in arabic.nsh for an example of a RTL language.
If your language uses special characters, use the corresponding ANSI code page.

Save the file under the name given by the rule in step 1.


===========================================================
** Third Step**
===========================================================
Open MUI\Language files\english.nsh in any text editor, and translate the strings between " ".

Use the same ponctuation, ie 
    use : when there is :
    use . when there is .
    use ... when there is ...

Save the file under the name given by the rule in step 1.
===========================================================
** Translation submission**
===========================================================
You can translate as many languages as you want, see the list of already translated languages, and post the file here as attachment :
Send us only the files you translated.

[http://ubuntuforums.org/showthread.php?t=457362](http://ubuntuforums.org/showthread.php?t=457362)

We strongly encourage you to post your work as well in the official NSIS forums, so they can be integrated in next releases of NSIS.
[http://forums.winamp.com/forumdisplay.php?s=&forumid=159](http://forums.winamp.com/forumdisplay.php?s=&forumid=159)

---

### Post by ecology2007 on 2007-05-28
Reserved space.

---

### Post by darkmaster on 2007-05-29
Hi, Italian translation is completed and controlled, see attachment. Everything is correct and OK. You did a nice work with this software, thanks!

---

### Post by open2linux on 2007-05-29
> **ecology2007 said:**
> If you want to translate wubi in your language, your contribution is welcome.:D
It is easy to do and it should not take you more than 20 minutes.
Send me a private message if you are interested.

See below in the attached file and post your work as attachment here :

I am not a programer, so please excuse me if what I tell you doesn´t make any sense.
But I see in the translation file that all lines start with:

LangString ...

And there are two lines apparently relating to the same thing, and one starts with

[COLOR="Red"];LangString AdvancedSettingsDistroToolTip ${LANG_ENGLISH} [/COLOR]

and the next one 

[COLOR="Red"]LangString AdvancedSettingsDistroToolTip ${LANG_ENGLISH} [/COLOR]

Is this OK? Or maybe some duplicating.

In any case I have translated it as it is, so you can easily fix the translation file if there is anything to be fixed at all.

Here is the Spanish translation. Happy to contribute a little with your wonderful project.

---

### Post by miketowninc on 2007-05-30
HI!!

I have transulated the file to GERMAN and im going to have my teacher correct it. She will do it for sure just give her a few days to correct. I used DEV-C which is only for C++ so i saved it for C++ i hope that is ok

Hope she gets it done soon.



love your program (Please fix the GRLDR i cant use it other wise)

peace

---

### Post by kynax on 2007-05-30
I'll work on the French translation.

I'll send it as soon as I complete it.

---

### Post by HampusW on 2007-05-31
You can now translate Wubi in a simpler way (the other still works fine though), using gettext files. You can use any po-file editor, eg. [poedit]("http://www.poedit.net/"). This only affects the format of the translation files, everything else still applies (see the first post, by ecology2007). I am one of the Wubi developers, by the way.

Instructions:
Download the attached wubi.pot and rename it to language.po, where "language" is the standard [language code]("http://www.gnu.org/software/gettext/manual/html_node/Language-Codes.html") for your language (eg. pt for Portuguese). Some of you might need to add a [country code]("http://www.gnu.org/software/gettext/manual/html_node/Country-Codes.html") (eg. pt_BR for Brazilian Portuguese). If you don't speak a special variant of a language you don't need to care about the country codes. In any case we can always change the name for you (if you would get it wrong), so don't think too much about that.

Now open the language.po file with your po-editor and translate it. You don't necessarily need to translate all the strings, even if that is recommended. When you are done with the translation and have saved the file, just send it to us (like you would with the language.nsh).

We can convert between the nsh-files and the po-files, so you can use whichever you prefer. I have used [poedit]("http://www.poedit.net/") myself for the Swedish translation and I think that is the easiest way to translate Wubi right now. We are in the process of setting up translation with rosetta at launchpad, but until then this is a good alternative.

Edit 2007-06-09: Updated instructions and pot-file.

---

### Post by kynax on 2007-05-31
Here is the French translation.

I haven't checked it in Wubi yet, but I'll give you feedback on it later.

I also noticed that the French translation has been set up in Launchpad but when I tried to use it, it gave me an error.

---

### Post by ecology2007 on 2007-06-02
Rosetta is being set up, it will take a couple of days before the files are uploaded.

---

### Post by jegHegy on 2007-06-02
Volunteering for hungarian translation.

---

### Post by jegHegy on 2007-06-04
Hungarian translation attached. Username and password tooltips have extra information added, namely directions not to use accented characters (in addition to the spaces originally mentioned).

Question:
;LoadLanguageFile "${NSISDIR}\Contrib\Language files\English.nlf"
Does the NullSoft installer have a Hungarian.nlf?

---

### Post by ecology2007 on 2007-06-04
> **jegHegy said:**
> Hungarian translation attached. Username and password tooltips have extra information added, namely directions not to use accented characters (in addition to the spaces originally mentioned).

Question:
;LoadLanguageFile "${NSISDIR}\Contrib\Language files\English.nlf"
Does the NullSoft installer have a Hungarian.nlf?

Yes, but we don't use it anyway, we have some custom code to handle translations. Lines that starts with ";" are disabled in the code, it does not matter if you translate it or not.

Thanks for your work.

---

### Post by fabiogramos on 2007-06-04
Brazilian Portuguese translation

---

### Post by Jordao on 2007-06-04
Here his the portuguese translation of wubi.

> **HampusW said:**
> You can now translate Wubi in a simpler way (the other still works fine though), using gettext files. You can use any po-file editor, eg. [poedit]("http://www.poedit.net/"). This only affects the format of the translation files, everything else still applies (see the first post, by ecology2007).



I used the poEdit method. I hope there isn't any problem...

---

### Post by true_friend on 2007-06-07
Hi folks.
This is Urdu (Pakistan) Translation of Wubi. Hope It is not too late.
Regards
True_Friend
[ATTACH]34672[/ATTACH]

---

### Post by ecology2007 on 2007-06-08
No, it s not too late, but your language is not supported by our programing system.
We can do it if you translate some extra files, it will be better if we ask the NSIS programmers to add support for pakistan.
[http://forums.winamp.com/forumdisplay.php?s=&forumid=159](http://forums.winamp.com/forumdisplay.php?s=&forumid=159)
I can explain you how to do it if you are interrested.

---

### Post by true_friend on 2007-06-08
Ohhh. No support of Arabic based languages.....
But windows xp has the support of Urdu Paksitan. This application will run under windows so it should be able to show.............
anyhows.... what can i do except coding because i am not a programmer.
Regards

---

### Post by rmzelle on 2007-06-09
Here is the Dutch translation:

---

### Post by ecology2007 on 2007-06-09
Master translation file has been updated, see first post of this thread.

---

### Post by miketowninc on 2007-06-09
Just to tell you I am still doing the German part and my teacher is grading it. Which is good but she doesnt understand PC to well to it takes longer. should have it by next wednessday.

---

### Post by miketowninc on 2007-06-09
I think you should add a thing at the end with the person who translated can put their name and email so people can send back feedback. just an idea

---

### Post by fabiogramos on 2007-06-09
Here is the new version from Brazilian Portuguese

---

### Post by rmzelle on 2007-06-10
New version in Dutch:

---

### Post by ecology2007 on 2007-06-10
Rmzelle : ok, it has been merged.
fabiogramos : I think you have made a mistake with zipping portuguese.nsh instead of portuguesebr.nsh.

---

### Post by ecology2007 on 2007-06-10
> **true_friend said:**
> Ohhh. No support of Arabic based languages.....
But windows xp has the support of Urdu Paksitan. This application will run under windows so it should be able to show.............
anyhows.... what can i do except coding because i am not a programmer.
Regards
Procedure is available here :
[http://ubuntuforums.org/showpost.php?p=2737747&postcount=3](http://ubuntuforums.org/showpost.php?p=2737747&postcount=3)

---

### Post by kynax on 2007-06-10
Here is the updated French translation.

Really looking forward to Rosetta being set up. Working in text files like this isn't so great...

---

### Post by fabiogramos on 2007-06-10
> **ecology2007 said:**
> Rmzelle : ok, it has been merged.
fabiogramos : I think you have made a mistake with zipping portuguese.nsh instead of portuguesebr.nsh.

oh yes, here is the right file

---

### Post by Jordao on 2007-06-11
Updated Portuguese translation

---

### Post by ecology2007 on 2007-06-11
Fabiogramos : ok it has been merged.
Jordao : you let a few strings in english, i did a copy paste of the fabiogramos version for them. You can check and send an updated version if you want.

---

### Post by nazo on 2007-06-11
here is japanese translation.
need to convert from utf-8 to shift_jis for nsis.

---

### Post by Jordao on 2007-06-11
> **ecology2007 said:**
> 
Jordao : you let a few strings in english.

Ups, here it goes the last version...

If something is wrong send me a private message

---

### Post by open2linux on 2007-06-11
**Update June 9 th 2007.**

Here is the edited Spanish translation as the June 9th update.

---

### Post by ecology2007 on 2007-06-11
> **kynax said:**
> Here is the updated French translation.

Really looking forward to Rosetta being set up. Working in text files like this isn't so great...

I already had the french translation, i should have warned you first.
Here is the previous version, check if you want to mix it with yours, and post here the result as usual.
I bundle you both.
You can use either poedit or direct editing of nsh.

---

### Post by zjtopspeed@gmail.com on 2007-06-12
Here is Simplified Chinese version:

---

### Post by ecology2007 on 2007-06-13
Your translation was based on an old version, i added the new strings and tried to keep as much as i can from your work.
Can you complete this one ?

---

### Post by zjtopspeed@gmail.com on 2007-06-13
here is the new version

---

### Post by miketowninc on 2007-06-14
Heres the German version. People can email me if they have a problem with the translation.

---

### Post by ecology2007 on 2007-06-14
Thanks a lot to miketowninc and zjtopspeed

---

### Post by bogdanco on 2007-06-21
Howdy guys, here is the Romanian translation, po style. Hope it's ok.

Best regards, 
Bogdan

---

### Post by Silav on 2007-06-26
Here is the Danish translation

---

### Post by swellwin on 2007-06-28
Here is the  TradChinese   translation

---

### Post by jegHegy on 2007-07-10
Attached latest hungarian translation.

---

### Post by Joshas on 2007-07-15
Hi, here's Lithuanian translation in gettext (po) format. I've translated it using Launchpad, and only then noticed that it is not quite supported, or is it?

---

### Post by swellwin on 2007-07-17
This  is new TradChinese  translations.

---

### Post by ecology2007 on 2007-07-20
Lithuanian, Bulgarian and Tradchinese have been succesfully merged.

---

### Post by Che_GueVaRRista on 2007-08-06
Hello,


Just translated to serbian, it should be attached to the file below,


txs, C.

---

### Post by Che_GueVaRRista on 2007-08-10
[SIZE="3"][COLOR="Olive"]Any chance of knowing when we'd be able to see it working in new version???[/COLOR][/SIZE]

---

### Post by ago on 2007-09-18
Hi all, I have uploaded the new files for the upcoming gutsy version

[http://codebrowse.launchpad.net/~ubuntu-installer/wubi/gutsy/files/ago%40nb-ago-20070918223140-f2msxy3awyvdjy4d?file_id=po-20070529205356-9mvslu0v3aodhtoy-3](http://codebrowse.launchpad.net/~ubuntu-installer/wubi/gutsy/files/ago%40nb-ago-20070918223140-f2msxy3awyvdjy4d?file_id=po-20070529205356-9mvslu0v3aodhtoy-3) 

Please update the po files if you can and attach them here. They should be mostly the same.

Please avoid to use the names "Ubuntu" and "Wubi" since the new version should be easy to rebrand. At the moment we have only one tooltip with the distro descriptions.

---

### Post by mikelpascual on 2007-09-27
Hi

I already translated wubi in rosetta some time ago, but I saw this post, so I'll post it here.

my language is Basque (eu).

I changed a pair of things from the rosetta translation (there was a pair of typos :p)


also, how could I get noticed about changes in the wubi pot, so I could quickly complete again the translation?

regards

---

### Post by hums07 on 2007-10-06
Indonesian translation

---

### Post by rmzelle on 2007-10-07
Here is the updated Dutch locale.

---

### Post by fr.hwang on 2007-10-15
Hi! I have translated NSH files in Korean.
A uploaded zip file has two directories:
[LIST]
[*]new(Gusty) - For updated version of Wubi.
[*]older - For current downloadable version of Wubi.
[/LIST]

I have reviewed the translated files in twice.
But if you have any problems, please contact me by e-mail.

Thank you for your great software!

- **Hyunseok Hwang ** from Republic of Korea. ( fr.hwang(AT)gmail.com )

---

### Post by gaffer_65 on 2007-10-25
Bulgarian translation, .nsh and .po flles

---

### Post by boban984 on 2007-10-25
This is the Macedonian translation (.nsh file)

Boban

---

### Post by YaronSh on 2007-11-03
The funny thing is that im also the official translator of NSIS (the translation was later fixed by one of the main NSIS programmers who also happens to be a Hebrew Speaking Israeli)
 
Anyways there it is!
I hope to see this implemented anytime soon!
 
Best Regards,
--- Yaron

---

### Post by ago on 2007-11-03
I have been focusing on the bug fixes for the time being, I'll merge all new translations soon. Thanks a lot to all!

---

### Post by shafin on 2007-12-14
Hope its not too late.
Here is the Bangla(bn) Translation

---

### Post by Joshas on 2008-01-03
Here's updated Lithuanian version. Better late than never ;) .

---

### Post by rlent on 2008-02-01
This is the Norwegian bokmål translation (no_bo.po)

---

### Post by ago on 2008-02-01
I am updating the translations mechanism, hopefully we'll be able to use rosetta.
Some translations will also change in 8.04. So bear with me for a few days. I will give you an update on the situation soon.

Thanks again to all translators!

---

### Post by mrv on 2008-02-22
> **ago said:**
> I am updating the translations mechanism, hopefully we'll be able to use rosetta.
Some translations will also change in 8.04. So bear with me for a few days. I will give you an update on the situation soon.

Thanks again to all translators!

Hi! What's the current status? I translated the 61 strings available in Rosetta to Finnish (fi), also attached. I know they're not necessarily (all) the strings that would be needed to be translated, but did it anyway to have at least some kind of start while waiting for the latest information what actually should be done...

The whole thing should hopefully be translatable as soon as possible, so that the translations may also be tested by 8.04 development version users.

---

### Post by ago on 2008-02-22
I have almost finished rewriting the new wubi for 8.04 (should be in the new alpha 5). 

I will then wait one or two days for comments on ENGLISH strings within wubi (any hint welcome)

Then will do a bit of cleanup and upload a new pot file in rosetta. 

All that within next week. 

I would like to have all translations in for beta

Once we are at it, the umenu project also needs some love :D

It is the small window that appear on the Ubuntu CD (first ever Ubuntu application Windows users will see!).  

[https://wiki.ubuntu.com/HardyHeron/Alpha5#head-208e566af858c79eaac897215bdf608edc5588a3](https://wiki.ubuntu.com/HardyHeron/Alpha5#head-208e566af858c79eaac897215bdf608edc5588a3)

---

### Post by mrv on 2008-02-25
> **ago said:**
> I have almost finished rewriting the new wubi for 8.04 (should be in the new alpha 5). 


Great!

> Once we are at it, the umenu project also needs some love :D

Yeah, I actually [filed a bug (bug #194337)](https://bugs.launchpad.net/umenu/+bug/194337) about it missing i18n :) But it would indeed be great to have that localized soon, too.

---

### Post by ago on 2008-02-25
> **ago said:**
> I will then wait one or two days for comments on ENGLISH strings within wubi (any hint welcome)

If anyone would like to help review the ENGLISH text in wubi/umenu please see the following 2 files:

[http://bazaar.launchpad.net/~ubuntu-installer/wubi/hardy/annotate/agostino.russo%40gmail.com-20080225023058-shsf3oawibio0nxt?file_id=english.nsh-20070529205356-9mvslu0v3aodhtoy-1](http://bazaar.launchpad.net/~ubuntu-installer/wubi/hardy/annotate/agostino.russo%40gmail.com-20080225023058-shsf3oawibio0nxt?file_id=english.nsh-20070529205356-9mvslu0v3aodhtoy-1)

[http://bazaar.launchpad.net/~ubuntu-installer/umenu/devel/annotate/evand%40ubuntu.com-20080220141346-5prmrb6va03jdtw1?file_id=english.nsh-20080212233008-kvy2sm0usmkk5nf3-18](http://bazaar.launchpad.net/~ubuntu-installer/umenu/devel/annotate/evand%40ubuntu.com-20080220141346-5prmrb6va03jdtw1?file_id=english.nsh-20080212233008-kvy2sm0usmkk5nf3-18)

Feel free to post here any suggestion

---

### Post by mrv on 2008-02-29
> **ago said:**
> 
[http://bazaar.launchpad.net/~ubuntu-installer/wubi/hardy/annotate/agostino.russo%40gmail.com-20080225023058-shsf3oawibio0nxt?file_id=english.nsh-20070529205356-9mvslu0v3aodhtoy-1](http://bazaar.launchpad.net/~ubuntu-installer/wubi/hardy/annotate/agostino.russo%40gmail.com-20080225023058-shsf3oawibio0nxt?file_id=english.nsh-20070529205356-9mvslu0v3aodhtoy-1)
[http://bazaar.launchpad.net/~ubuntu-installer/umenu/devel/annotate/evand%40ubuntu.com-20080220141346-5prmrb6va03jdtw1?file_id=english.nsh-20080212233008-kvy2sm0usmkk5nf3-18](http://bazaar.launchpad.net/~ubuntu-installer/umenu/devel/annotate/evand%40ubuntu.com-20080220141346-5prmrb6va03jdtw1?file_id=english.nsh-20080212233008-kvy2sm0usmkk5nf3-18)


I went through those briefly and thought that they were very good... I didn't find anything to complain, though it's easier to spot problems in a running program of course.

Keep up the great work!

---

### Post by rmzelle on 2008-02-29
I downloaded the newest Hardy release, and I must admit I find the umenu quite confusing. None of the buttons give a clear indication of what pressing them will do. I think it should be made clearer that pressing the first button won't restart your computer, that the second one will only move you to an installer screen but won't immediately install anything, and that the third button is actually a hyperlink.

The umenu should probably use "quit" instead of "cancel".

Clicking cancel in either the CD-boot-helper installer or wubi-installer should probably move you back to the umenu as well.

Finally I found the "Access"-button in wubi very strangely placed next to the install button.

---

### Post by ago on 2008-03-01
> **rmzelle said:**
> I downloaded the newest Hardy release, and I must admit I find the umenu quite confusing. None of the buttons give a clear indication of what pressing them will do. I think it should be made clearer that pressing the first button won't restart your computer, that the second one will only move you to an installer screen but won't immediately install anything, and that the third button is actually a hyperlink.

The umenu should probably use "quit" instead of "cancel".

Clicking cancel in either the CD-boot-helper installer or wubi-installer should probably move you back to the umenu as well.

Finally I found the "Access"-button in wubi very strangely placed next to the install button.

rmzelle all valid points, unfortunately we are past UI freeze. 
All we can do at this point is change the text strings. If you have any specific suggestion in that regard please post it.
I'd suggest opening a umenu/wubi bugs in launchpad anyway

---

### Post by rmzelle on 2008-03-01
> **ago said:**
> If you have any specific suggestion in that regard please post it.

Some suggestions:

"Demo and full installation" > "Run Ubuntu from the Live CD..."
(the dots indicate there is at least another dialog screen before any action is taken, see [http://www.linfo.org/dot.html](http://www.linfo.org/dot.html))

"Try Ubuntu without installing! Simply reboot your machine with the CD in the tray. You will later have the option to perform a full installation from within the demo itself."
>
"Try Ubuntu without installing! After booting from the Ubuntu CD, you will have the option to perform a full installation of Ubuntu to a local drive."

"Install inside Windows"  > "Install within Windows..."

"You can install Ubuntu without modifying your disk setup. Suspend and hibernation are not enabled in this mode and performance is slightly reduced. Uninstalling again is easy."
>
"You can install Ubuntu within Windows without the need for a separate drive partition. In this mode suspend and hibernation are not enabled and performance is slightly reduced. Uninstalling again is easy."

"Learn more" > "Visit the Ubuntu website"

"Ubuntu is a free operating system complete with web browser and productivity software. These applications are also available and free for Windows."
>
"Ubuntu is a free operating system complete with web browser and productivity software. Learn more about Ubuntu by visiting the Ubuntu website."
(As I couldn't easily find the free applications for Windows on the Ubuntu website, I suggest leaving out the last sentence.)

---

### Post by ago on 2008-03-01
Thanks for the suggestions. I'll explain my reasoning behind current choices:

The main point that the page is supposed to be perused by non-technical users, hence I'd like to avoid any terms such as "partitions", "ISO", "MBR", "Bootloader", "Live CD"... and keep the text as simple as possible. 

"Demo and Full Installation"

I still like that better, since most windows users do not know what a "live" CD is, with "Demo and Full Installation" there isn't much to explain. Moreover if the words "Full Installation" are not in there many will think that Wubi is the main installation route (cannot trust users to read the small text) while the recommended long term installation is the one to dedicated partition. 

"without modifying your disk setup"

If I really wanted to be precise that should be something like "without touching the partition table or the MBR", but, as mentioned, being technically precise is not the objective... 

Winfoss:

The final CD might have some built-in static web pages, with references to both Ubuntu and Winfoss. If it doesn't then I agree we should remove that comment.

---

### Post by rmzelle on 2008-03-02
> **ago said:**
> The main point that the page is supposed to be perused by non-technical users, hence I'd like to avoid any terms such as "partitions", "ISO", "MBR", "Bootloader", "Live CD"... and keep the text as simple as possible. 

"Demo and Full Installation"

I still like that better, since most windows users do not know what a "live" CD is, with "Demo and Full Installation" there isn't much to explain. Moreover if the words "Full Installation" are not in there many will think that Wubi is the main installation route (cannot trust users to read the small text) while the recommended long term installation is the one to dedicated partition.

I still think the dots should be there ("Demo and Full Installation...").

It's just that I think of the LiveCD option as more than a demo, as Ubuntu is fully functional in that mode, right? By the way, I didn't see any system requirements listed for Ubuntu, either for the Live CD or the full installation.

I agree that jargon should be kept to a minimum, but I also think it should be clear to technical users what the different options really mean.

> **ago said:**
> 
"without modifying your disk setup"

If I really wanted to be precise that should be something like "without touching the partition table or the MBR", but, as mentioned, being technically precise is not the objective...

Perhaps a link to some additional info would be helpful for more technical users? e.g.:

"You can install Ubuntu without modifying your disk setup. Suspend and hibernation are not enabled in this mode and performance is slightly reduced. Uninstalling again is easy. Learn more about this type of installation by visiting http://wubi-installer.org/."

---

### Post by v1cho on 2008-03-03
Is it a problem that some translated strings are too long? :confused:
I'm just translating it into Bulgarian :)

---

### Post by ago on 2008-03-03
> **v1cho said:**
> Is it a problem that some translated strings are too long? :confused:
I'm just translating it into Bulgarian :)

You have to look at the Wubi interface and try to guess, in any case you should have an option to change the translations after they are incorporated into wubi.

---

### Post by ago on 2008-03-03
Have updated Rosetta, can someone pls try to provide 1 full file, I'll check if everything works well. Please do not submit files anymore, but instead use Rosetta. Hopefully it will make things easier for anyone.
 
[https://translations.launchpad.net/wubi/trunk](https://translations.launchpad.net/wubi/trunk)

Umenu will follow shortly after: 1) I test the rosetta setup in wubi, 2) we agree on the above comments.

---

### Post by v1cho on 2008-03-03
I hope Wubi works with wine, I don't have windows  on this machine :)

P.S. I was just editing the attachment form the first post... Does this Rosetta thing mean that I'll have to start over translating it :?

P.S. 2 Where do I download Wubi 7.10 from? On the official site the version is 7.04 ...

---

### Post by ago on 2008-03-03
> **v1cho said:**
> I hope Wubi works with wine, I don't have windows  on this machine :)

P.S. I was just editing the attachment form the first post... Does this Rosetta thing mean that I'll have to start over translating it :?

I have uploaded the po files I had available, and (thanks to Hampus) also have nsh-to-po translator (but have not migrated all nsh files). Consider that in any case, quite a few strings have changed, so any pre-existing po would be used as a starting point anyway.

---

### Post by v1cho on 2008-03-03
> **ago said:**
> I have uploaded the po files I had available, and (thanks to Hampus) also have nsh-to-po translator (but have not migrated all nsh files). Consider that in any case, quite a few strings have changed, so any pre-existing po would be used as a starting point anyway.

Uhmmm what? :D Sorry, but I'm not familiar with po and other stuff... Can you explain it simpler, should I retranslate it in Rosetta?

---

### Post by ago on 2008-03-03
> **v1cho said:**
> Uhmmm what? :D Sorry, but I'm not familiar with po and other stuff... Can you explain it simpler, should I retranslate it in Rosetta?

That would be the easier route probably. If you let me know about nsh files that are not in there I can try to convert them and import them into rosetta (it may take a few days). But I would not think it would be too much of an advantage. There isn't any need to know much about pot/po/gettext, since the rosetta web interface is quite handy and intuitive.

---

### Post by mrv on 2008-03-04
> **ago said:**
> Have updated Rosetta, can someone pls try to provide 1 full file, I'll check if everything works well.

Finnish (fi) is now fully translated:

[https://translations.launchpad.net/wubi/trunk/+pots/wubi/fi/+translate](https://translations.launchpad.net/wubi/trunk/+pots/wubi/fi/+translate)

Note that I noticed one spelling mistake: "Kubuntu-KD4 uses the KDE4 desktop."

---

### Post by rmzelle on 2008-03-04
Ago,

I added another proposal for the umenu on the wiki ([https://wiki.ubuntu.com/umenu](https://wiki.ubuntu.com/umenu)). I understand you can't change the UI for 8.04, but it be helpful for later releases. Notable changes:

- The UI doesn't rely that much on the texts on buttons
- The LiveCD and full install are clearly distinguished options
- The menu now start with a welcoming message, including the version number of the Ubuntu release

---

### Post by ago on 2008-03-04
Nice work! I'll point other devs to that too to see if there are ideas to use.
As mentioned though GUIs are now in feature freeze. So I'd guess it will mostly be a matter of wordings.

---

### Post by nDrewPJ on 2008-03-04
I've just finished Russian translation. :popcorn:
Check the attachment. Couldn't upload with Launchpad.net :(

---

### Post by ago on 2008-03-04
Thanks! Will try to upload later on today!

---

### Post by ago on 2008-03-04
One good news and one bad news...

Good news is that the your new translations are in wubi (rev447), so you can already test them out.

The bad news is that there the wubi.pot file was not complete, and quite a few strings were missing. So you might have to add some translations. The new pot should be available soon on rosetta. 

[https://translations.launchpad.net/wubi/](https://translations.launchpad.net/wubi/)

---

### Post by ago on 2008-03-05
Please use this thread [http://ubuntuforums.org/showthread.php?t=716056](http://ubuntuforums.org/showthread.php?t=716056) for any issue relating to 8.04 translations.

---

