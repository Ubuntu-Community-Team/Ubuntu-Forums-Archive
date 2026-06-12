---
title: "Who to modify Wubi for an Ubuntu like distribution ?"
date: 2008-01-30
forum: General Help
---

### Post by mirage59 on 2008-01-30
Hello everybody,
I love an ubuntu like french distribution (i'm french)

it's name is "NuNuX"[ http://nunux-fr.org/forum/index.php]("http://nunux-fr.org/forum/index.php")

I want to modify wubi because he can't install NuNuX :(

Somebody can help me ? Why files a must modify (I have already modify the .metalink to download NuNuX) ?

Thanks you for your help :)

---

### Post by ago on 2008-01-30
Basically the most relevant files/folders are

wubi/src/inspector/isolist.ini
wubi/src/dist/install/metalinks
wubi/src/translations 
wubi/src/version.nsh

I will recode in the future to make it easier to customize. Let me know if you have any question. I will also remove ubuntu specific localizations.

---

### Post by ago on 2008-01-30
to compile, use linux:

#first time only
make prerequisites
make plugins
make wubildr
make translations
#after new changes
make

---

### Post by mirage59 on 2008-01-30
Thanks you for your quick answer :)

I have modify :

wubi/src/inspector/isolist.ini       [Add an entry for NuNuX]
wubi/src/dist/install/metalinks     [Add an .metalink file for download NuNuX]

But why I must modify :

wubi/src/translations     [For the moment I'm not preoccupated by the language 
**if** I can make a good installation ;) ]
wubi/src/version.nsh    [aside "DistroName""DistroVersion" and "DistroSubversion" ?]


?
And can you explain me your second message ?

"to compile, use linux:

#first time only
make prerequisites
make plugins
make wubildr
make translations
#after new changes
make"

I don't understand what I must do :s

Thanks you very very much :)

---

### Post by ago on 2008-01-30
> **mirage59 said:**
> But why I must modify :

wubi/src/translations     [For the moment I'm not preoccupated by the language 
**if** I can make a good installation ;) ]

Any string you see is a template defined in translations (english). So if you want to change any text, that's the place. Whether you then get localized is a separate issue.

> 
wubi/src/version.nsh    [aside "DistroName""DistroVersion" and "DistroSubversion" ?]

That contains other things such as name of the program, version, installation folder, boot menu name etc you may want to change

> I don't understand what I must do :s

Thanks you very very much :)
Grab the source files using bzr
Go into the main wubi folder
Run the commands in the order specified

---

### Post by mirage59 on 2008-01-30
> **ago said:**
> 
Grab the source files using bzr
Go into the main wubi folder
Run the commands in the order specified

Sorry,but my english is not very good
I don't understand this "Grab the source files using bzr"

And when I enter "cd /media/sda5/Wubi-7.04.04-src/wubi/testing" in a terminal ,to go to the wubi folder, and after I enter "make prerequisites" a have an error, it's in french, like :
"make: *** No rule to do the target « prerequisites ». Stop."

I think I made an error, can you help me :$

---

### Post by ago on 2008-01-30
sudo apt-get install bzr
mkdir wubi
cd wubi
bzr branch [http://bazaar.launchpad.net/~ubuntu-installer/wubi/hardy](http://bazaar.launchpad.net/~ubuntu-installer/wubi/hardy)
cd hardy
make prerequisites
make plugins
make translations
make

---

### Post by mirage59 on 2008-01-31
I have installed "bzr", created the wubi folder and go to it but
When I enter "bzr branch http://bazaar.launchpad.net/~ubuntu-...ler/wubi/hardy"

The terminal send me "bzr: ERROR: Not a branch: http://bazaar.launchpad.net/~ubuntu-...ler/wubi/hardy/" 

And if I try to fo to the link with firefox I have a 404 error :-(

Sorry for my debility :$
Thanks for your time and your help

---

### Post by ago on 2008-01-31
right click on the link, copy the link address and use that. The forum abbreviates the url.

---

### Post by mirage59 on 2008-01-31
Excuse me for my noobs error :

 I have paste the good link : "http://bazaar.launchpad.net/~ubuntu-installer/wubi/hardy" but the terminal send me an another error like 

"bash: [http://bazaar.launchpad.net/~ubuntu-installer/wubi/hardy:](http://bazaar.launchpad.net/~ubuntu-installer/wubi/hardy:) none file or folder of this  type"

:(

---

### Post by ago on 2008-01-31
inside wubi folder type
bzr branch "http://bazaar.launchpad.net/~ubuntu-installer/wubi/hardy" hardy

---

### Post by mirage59 on 2008-01-31
Thanks you very much

A last question : I have do all, but I can't find the executable files, Where is the .exe to open in Windows xp ?

Thanks you

---

### Post by ago on 2008-01-31
under dist

---

### Post by mirage59 on 2008-01-31
My folder "dist" is empty :-k

When I saw that I try to redo :" bzr branch "http://bazaar.launchpad.net/~ubuntu-installer/wubi/hardy" hardy"

But my Folder remain empy :( :sad:

Do you have an answer ?

---

### Post by ago on 2008-02-02
that gets filled when you run make

---

### Post by st3reo on 2008-10-05
Hello,

I'm having some trouble compiling the Wubi source.
I`ve made some minor modifications in order to support a ubuntu derrivate but when I compile I get an error at the **make translations** part

> 
./tools/translate "src/wubi/english.nsh" "po/wubi.pot" "po" "build/translations" "po/ignore.po"
DEBUG:translate:['./tools/translate', 'src/wubi/english.nsh', 'po/wubi.pot', 'po', 'build/translations', 'po/ignore.po']
DEBUG:translate:nsh2pot /usr/local/src/source/src/wubi/english.nsh -> /usr/local/src/source/po/wubi.pot
DEBUG:translate:Updating generated file.
bzr: ERROR: Not a branch: "/usr/local/src/source/".
Traceback (most recent call last):
  File "./tools/translate", line 97, in <module>
    update_all(*args)
  File "./tools/translate", line 89, in update_all
    nsh2pot(nshtemplate, potfile, poignore)
  File "./tools/translate", line 60, in nsh2pot
    text = text.replace('VERSION', str(bzr_revno()))
  File "./tools/translate", line 37, in bzr_revno
    return int(child_stdout.readline())
ValueError: invalid literal for int() with base 10: ''
make: *** [translations] Error 1



Could anyone please help?
Thanks,

---

### Post by ago on 2008-10-06
st3reo did you use bazaar to grab the wubi sources or did you use a tgz? You need bzr. 

bzr branch lp:wubi

---

### Post by st3reo on 2008-10-06
I used the .tgz from the sourceforge page.

I'm not familliar with bazaar, could you please detail **bzr branch lp:wubi ** a bit..especially the **ip:wubi** part.

Thanks a lot.

---

### Post by ago on 2008-10-06
that is just the command you have to type into ubuntu to get the source code... it is Lp not Ip, Lp = launchpad

---

### Post by sohaibafifi on 2009-07-07
Try :
bzr branch lp:wubi

---

