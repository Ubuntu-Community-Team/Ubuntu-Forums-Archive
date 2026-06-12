---
title: "The last barrier for converting my whole workplace to Ubuntu - wine help needed!"
date: 2007-05-12
forum: General Help
---

### Post by Jh00 on 2007-05-12
Hi there,

I was very excited when my Boss told me that I could install Ubuntu at our workplace... (20 PCs) until he said "however, you must make MyBase work as well". 

Oh well.. MyBase is a little windows app ([www.wjjsoft.com](www.wjjsoft.com)) for knowledge management that we use to store documents and webpages for later retrieval. We have a dozen databases already fully categorized, so converting it to, say, a mysql system is not an option.

I tried running it under wine and, although the software ran, there is a little problem that I still could not fix: it seems that MyBase uses an embeded "version" of Internet Explorer to display the stored webpages in its window. Since there is no native IE in this setup, the webpages don't show up.

This "embeded IE thing" is very commonly used in lots of programs that need to display HTML content, so I thought that maybe this could be a trivial fix. Does anyone know how could I make this work?

I thank you very much in advance! I very much wanted to have Ubuntu at my workplace.

J.

---

### Post by strabes on 2007-05-12
Is there a reason why you can't just [install IE](http://www.google.com/search?q=install+IE+with+wine&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a) with wine?

---

### Post by YokoZar on 2007-05-12
There are two ways to make Internet-Explorer dependent programs work in Wine.  The first is to allow Wine to use Mozilla's gecko rendering engine as a substitute for Internet Explorer.  This is how steam is made to work out of the box, but this approach doesn't always work for applications that use internet-explorer specific features (or bugs) that aren't found when using a gecko browser like Firefox.

In that case, you'll need to install IE with Wine.

---

### Post by Jh00 on 2007-05-12
Hi there, thanks for the answers.

After I installed gecko and IE, the window where the html page should appear was simply blank - nothing happened. As for IE, I couldn't get it to work either. 

Any hint as which version of IE should I try? Anyone had success with running an application like the one I mentioned under wine?

Thanks!

---

### Post by Enverex on 2007-05-12
IE doesn't work in Wine normally, it requires a lot of arsing about and basically breaking Wine so lets see if the proper method works first.

Try - wine iexplore [http://www.winehq.org](http://www.winehq.org)

and see if that displays the site. Also make sure you've added the IE fake registry entries into Wine's registry (see the FAQ in my sig).

---

### Post by YokoZar on 2007-05-13
If you have both gecko and IE installed, you'll need to configure Wine to use IE's dlls rather than Wine's built-in ones.  Do this by setting a few things in winecfg to native - I'm not sure which ones in particular, but you can find this on one of the links here or in the AppDB

---

### Post by lamadredelsapo on 2007-05-13
Have yout tried IES4linux? It's a script that installs IE 6, 5.5 and 5.0

Take a look at [[COLOR="Red"]IES4Linux[/COLOR]]("http://www.tatanka.com.br/ies4linux/page/Main_Page")

---

### Post by Enverex on 2007-05-13
> **lamadredelsapo said:**
> Have yout tried IES4linux? It's a script that installs IE 6, 5.5 and 5.0

Take a look at [[COLOR="Red"]IES4Linux[/COLOR]]("http://www.tatanka.com.br/ies4linux/page/Main_Page")

That installs into a seperate "WINEPREFIX" and wont help.

---

### Post by lamadredelsapo on 2007-05-13
Ooh! I didn't know that...

---

### Post by Jh00 on 2007-05-13
Ok, I gave it another shot. 

Running wine iexplore [http://www.winehq.org](http://www.winehq.org)  like Enverex suggested worked. However, MyBase isn't working - when I click on an entry, a popup error with nothing written at all appears, and nothing is displayed. The console shows up the following error.

> 
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGING: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGED: stub
fixme:richedit:RichEditANSIWndProc ECO_AUTOWORDSELECTION not implemented yet!
fixme:richedit:RichEditANSIWndProc EM_SETTARGETDEVICE: stub
fixme:shdocvw:WebBrowser_Stop (0x7073a8)


I'm starting to wonder if MyBase doesn't deppend onto some library that is not yet implemented in Wine... Could anyone tell me anything about those errors?

I'm sorry to press this subject on this forum - but I could not find a Wine forum to ask to... 

Thanks in advance!
Júlio

---

### Post by david_kt on 2007-05-13
> **Jh00 said:**
> Ok, I gave it another shot. 

Running wine iexplore [http://www.winehq.org](http://www.winehq.org)  like Enverex suggested worked. However, MyBase isn't working - when I click on an entry, a popup error with nothing written at all appears, and nothing is displayed. The console shows up the following error.



I'm starting to wonder if MyBase doesn't deppend onto some library that is not yet implemented in Wine... Could anyone tell me anything about those errors?

I'm sorry to press this subject on this forum - but I could not find a Wine forum to ask to... 

Thanks in advance!
Júlio

I have tried MyBase viewer works perfectly using wine. I could not managed to get the full software works though, It may be a little bit difficult. I will give a try another 2 weeks after my business trip.

In the mean time, Why don't you try to run Mybase viewer first and tell us what problem you face if you run mybase viewer? Is it possible that you use MyBase viewer for most computers and run full software only on 1 or 2 computers?

DK

---

### Post by Jh00 on 2007-05-14
Hmm... that sounds interesting.. I was wondering if the "piece" of Mybase that isn't working is just the Rich Text editor, and maybe that's why the viewer works (it doesn't edit anything). I will give it another try.

Even though viewing the DB would be a good option, I will still try to make the full app work. But thanks for the tip!

---

### Post by DizzyTech on 2007-05-14
I know it's against the point to use MSIE in WINE, and ies4linux was cast away, but why don't you install ies4linux and then run in a terminal (assuming you installed IE6) "cp -fr ~/.ies4linux/ie6/ ~/.wine" for copying, or "ln -s  ~/.ies4linux/ie6/ ~/.wine" for linking , and then install MyBase?

---

