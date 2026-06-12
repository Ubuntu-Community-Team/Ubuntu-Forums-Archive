---
title: "lyx and pybliographic"
date: 2005-08-23
forum: General Help
---

### Post by alastair lewis on 2005-08-23
I want to use and pybliographic and lyx for writing scientific papers. I have installed both and quite like lyx as a word processor.

My problem is inserting citations. The user manual for pybliographic states
[COLOR=Blue]To do so, one has to first start the lyx server. In the config file, ~/.lyx/lyxrc,add the following line.  \serverpipe "~/.lyx/lyxpipe"[/COLOR]

I do not have a lyxrc file or directory in ~/.lyx and I don't know how to start the server.

```
locate lyxrc
``` gives

/etc/lyxrc
/usr/bin/update-lyxrc
/usr/share/man/man1/update-lyxrc.1.gz
/usr/share/lyx/lyxrc.defaults
/usr/share/lyx/lyxrc.example

Without being able to find/insert/change/format citations it will be back to endnote/word. (I really don't want that). Can anyone help?

---

### Post by arnieboy on 2005-08-25
[QUOTE=alastair lewis]I want to use and pybliographic and lyx for writing scientific papers. I have installed both and quite like lyx as a word processor.

My problem is inserting citations. The user manual for pybliographic states
[COLOR=Blue]To do so, one has to first start the lyx server. In the config file, ~/.lyx/lyxrc,add the following line.  \serverpipe "~/.lyx/lyxpipe"[/COLOR]

I do not have a lyxrc file or directory in ~/.lyx and I don't know how to start the server.

```
locate lyxrc
``` gives

/etc/lyxrc
/usr/bin/update-lyxrc
/usr/share/man/man1/update-lyxrc.1.gz
/usr/share/lyx/lyxrc.defaults
/usr/share/lyx/lyxrc.example

Without being able to find/insert/change/format citations it will be back to endnote/word. (I really don't want that). Can anyone help?[/QUOTE]
I assume u know that ~/.lyx refers to the hidden directory ".lyx" in your home directory. this gets created when u start using lyx. 
if u dont have the lyxrc config file in that directory, u can simply copy the global config file from /etc (ie., /etc/lyxrc) to /home/usr_name/.lyx/ and also copy lyxpipe from wherever it is (use slocate) to the same directory and then add the line in your ~/.lyx/lyxrc file.  Please remember that the configuration in your home directory will take preference over your global preferences (in this case /etc/lyxrc).

---

### Post by alastair lewis on 2005-09-01
Thanks for that. I was happy with what /.lyx refered to.
I have created the lyxrc file, The server is up and running and pybliographic happily dumps citations into an open test file. However, when I view the file the citation appears as [?]. Not what I am after, for example.

[COLOR=Blue]In text of scientific paper citation number[1], followed at the end of the paper

Bibliography
[1] Arnieboy. Re:lyx and pybliographic. Ubuntuforums 2005
[/COLOR]
What I am chasing is a FLOSS alternative to endnote/word

---

### Post by arnieboy on 2005-09-01
[QUOTE=alastair lewis]Thanks for that. I was happy with what /.lyx refered to.
I have created the lyxrc file, The server is up and running and pybliographic happily dumps citations into an open test file. However, when I view the file the citation appears as [?]. Not what I am after, for example.

[COLOR=Blue]In text of scientific paper citation number[1], followed at the end of the paper

Bibliography
[1] Arnieboy. Re:lyx and pybliographic. Ubuntuforums 2005
[/COLOR]
What I am chasing is a FLOSS alternative to endnote/word[/QUOTE]
try using kile to compile latex docs with bibtex. its the closest u can get to winedit and it does a wonderful job with bib files and references. pybliographic is a good alternative to endnote and it can export as bib files pretty well.

---

### Post by parktownprawn on 2005-09-23
[QUOTE=alastair lewis]Thanks for that. I was happy with what /.lyx refered to.
I have created the lyxrc file, The server is up and running and pybliographic happily dumps citations into an open test file. However, when I view the file the citation appears as [?]. Not what I am after, for example.[/QUOTE]

Ok pybliographic just inserts the citation into lyx but it doesn't tell lyx what bibtex database to use. You have to do that.

In your lyx document  goto

Insert -> List & TOC -> Bibtex Bibliography 

then click on browse and go to the location of your bibtex file and add it in.

then when you view  the file it should work fine. Once lyx knows about your bibtex file you can insert citations into directly using Insert->Citation.

Lyx works really well with bibtex - infacts its one of the main reasons i like to use lyx.

---

### Post by alastair lewis on 2005-09-29
Thanks.

I have got up and running by creating a bibtex file with Pybliographic containing all the references I may want  and saving it. At a later stage I then do what you say with the Insert>>Lists&TOC>>bibtex file. I then cite away merrily once the article is written. I have a .bst file constructed for the British Journal of Surgery if anyone wants it.

I might give the cite as you write option another go but I like doing things the above way.

Lyx is great. Another triumph of the FLOSS community.

---

### Post by jakes on 2006-04-23
Hi, 
I realise this thread's a bit old and in the Warty section, but it pretty much applies to the problems I'm having with Lyx on Breezy, so I thought I'd post here rather than start a new thread.
I can't get the lyx server to start so that i can use pybliographer to manage and insert citations into my lyx documents. I've just installed LyX v 1.4.1 from the debs on the LyX site. I'm using Pybliographer 1.2.5, which is the version in the Breezy repos.
Basically I've followed the instructions in the second post in this thread. I moved lyxrc to ~/.lyx/lyxrc, and inserted the serverpipe line into the config file. But lyxpipe.in is not being created - I can't find it anywhere on my system to copy to the .lyx directory in my home folder. So it would seem something somewhere is broken. 
I had a look at the LyX user mailing list archive and there were some references there about making sure that the path to the lyxpipe file was correct, using Preferences>Path. But the preferences option does not have a 'Path' tab in my version of LyX. Has it been removed, or is something wrong with my install.
I'm not sure what else to do. If anybody has any suggestions (even if it's just to reinstall), I'd be most grateful, as I'd really like to get this working.
Cheers,
jakes.

---

### Post by parktownprawn on 2006-04-23
[QUOTE=jakes]Hi, 
I had a look at the LyX user mailing list archive and there were some references there about making sure that the path to the lyxpipe file was correct, using Preferences>Path. But the preferences option does not have a 'Path' tab in my version of LyX. Has it been removed, or is something wrong with my install.
[/QUOTE]

I cann't comment about lyx 1.4.  I'm using the version in breezy - 1.3.6. 

I have pybibliogrpaher and lyx working well together. In that version the path tab is the 4th one in the preferences menu.  You can just type in a path for the lyxpipe server using this menu.  

While its pybibliographer is nice for editing bibtex files i'm not sure I see the point of using it to insert citations into lyx. Its easy enough to do this with lyx itself. 

see
[http://wiki.lyx.org/uploads/BibTeX/biblioexample.pdf](http://wiki.lyx.org/uploads/BibTeX/biblioexample.pdf)

---

### Post by jakes on 2006-04-23
[QUOTE=parktownprawn]I cann't comment about lyx 1.4.  I'm using the version in breezy - 1.3.6. 
...
While its pybibliographer is nice for editing bibtex files i'm not sure I see the point of using it to insert citations into lyx. Its easy enough to do this with lyx itself. 

[/QUOTE]
Thanks for your reply, parktownprawn.You're right, I probably don't need to use Pybliographer to insert citations. After posting, I worked out how to do it from within LyX, but thanks for pointing me to that pdf. I'll have a look at it to see if I've missed something.
There must, however, be a reason that they offer a mechanism to insert citations from an external source. I'd still be interested in having the lyx server working to try it out to see if it does have any benefits, if anybody knows what to do.
cheers.

---

### Post by kleeman on 2006-04-23
Hmmm that's interesting. After I read your post I tried this again in lyx and in pybliographer as well as jabref (a java bibliography frontend). It did not work despite having all paths set up properly. So I deleted .lyxpipe.in and .lyxpipe.out then restarted lyx which recreated the files. After this both pybliographer and jabref were able to push citations to lyx.

---

### Post by jakes on 2006-04-23
[QUOTE=kleeman]Hmmm that's interesting. After I read your post I tried this again in lyx and in pybliographer as well as jabref (a java bibliography frontend). It did not work despite having all paths set up properly. So I deleted .lyxpipe.in and .lyxpipe.out then restarted lyx which recreated the files. After this both pybliographer and jabref were able to push citations to lyx.[/QUOTE]

You wouldn't, by any chance, have any suggestions as to what to do if the lyxpipe.in and lyxpipe.out files aren't being created at all? I can't find them (assume they should be in the ~/.lyx folder), so I'm not able to delete them to make lyx recreate them on restart.
Thanks.

---

### Post by kleeman on 2006-04-23
If you got to Edit---> Preferences----> Paths in lyx what does it say for LyxServer pipe? 

Mine says /home/username/.lyxpipe

which means the files you are looking for are in /home/username not in 
/home/username/.lyx

---

### Post by jakes on 2006-04-23
Thanks for your help, kleeman.
So here's the bizarre thing. I don't have a 'Paths' option in my preferences. In fact, Preferences is under 'Tools', not 'Edit'. The tabs under Tools>Preferences are:
Fonts
Language
Graphics
Spellchecker
Keyboard.

No 'Paths' option. This leads me to think that there's something wrong with my installation of LyX. I used your debs to install 1.4.1. There were some dependency problems initially, but I fixed them.
Just to make sure I checked my home directory (/home/username) for the .lyxpipe files. They weren't in there either. And without being able to set the Path, I'm not sure where they should be...

---

### Post by kleeman on 2006-04-23
Hmmm I installed 1.4.1 again and found it (Paths) OK (Tools---> Preferences). Try executing lyx-qt and see whether this makes a difference. Also check to make sure you have all the tetex packages installed. Also go into synaptic and right click on lyx-common and install all recommended packages.

---

### Post by jakes on 2006-04-23
[QUOTE=kleeman]Hmmm I installed 1.4.1 again and found it (Paths) OK (Tools---> Preferences). Try executing lyx-qt and see whether this makes a difference. Also check to make sure you have all the tetex packages installed. Also go into synaptic and right click on lyx-common and install all recommended packages.[/QUOTE]
Thanks so much for your help - I've managed to get it working following your suggestion. I used lyx-qt and the Paths option is in Preferences there (as well as other options that don't show up in gtk). The lyxpipe field was empty, so once I had set it, Pybliography was able to connect.
I checked in Synaptic and all the recommended packages for lyx-common are already installed, so it would seem that the lyx-gtk version simply doesn't expose all the options in the Preferences menu. Setting the correct path in the qt package, has made it work in the gtk version though.
Thanks again,
jakes.

---

### Post by parktownprawn on 2006-04-24
since the  gtk-version  is new i guess there are some extra user-interface bugs/features to iron out.

---

