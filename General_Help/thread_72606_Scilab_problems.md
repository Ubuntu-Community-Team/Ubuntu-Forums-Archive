---
title: "Scilab problems"
date: 2005-10-06
forum: General Help
---

### Post by sawjew on 2005-10-06
I don't know if anyone here can help me but I have a problem with Scilab.

I am new to scilab, having been a Matlab user at university, and I have just installed scilab on an Ubuntu Breezy system.  My problem is that when I open the command window all I see is some unknown script rather than any intelligible language.  I don't know if it is displaying in another language or just gibberish but it is currently unusable.  does anyone have any idea how to fix this?

the menus and graphics window and editor are fine.

any help would be greatly appreciated.

---

### Post by cvrancken on 2005-10-08
I'm having exactly the same problem.

All I could do was edit the /usr/lib/scilab/bin/scilab file. Down there in the middle:

# calling Scilab with no argument or special cases of calling Scilab
rest="no"
case $# in
    0)
       $SCI/bin/zterm -f fixed -e $SCI/bin/scilex $start_file $arguments &
        ;;

(I added the "-f fixed" option to zterm. zterm doesn't like that much, but scilab shows up anyways with some font... really really small for my screen, but better than the unreadable font for sure).

Any other suggestions?

C.

---

### Post by nsa_767 on 2005-10-09
Hi, 

I know this isn't exactly a proper solution, but try and use maxima or octave instead of scilab until you've gotten things sorted....

Personally, I've never been able to figure scilab out.... But then, I have no matlab experience either.

Maxima is an excellent general purpose CAS, and Octave is extremely good with working with vectors... I also think Octave might have some (limited) matlab compatibility....

BTW: Someone should really start an area in the ubuntu forums for scientific apps and the like... If we all could get together, we might be able to get more of these apps (and up-to-date versions) into the repositories.

Not that I'm saying ubuntu is lacking in this area....

---

### Post by sawjew on 2005-10-10
[QUOTE=cvrancken]I'm having exactly the same problem.

All I could do was edit the /usr/lib/scilab/bin/scilab file. Down there in the middle:

# calling Scilab with no argument or special cases of calling Scilab
rest="no"
case $# in
    0)
       $SCI/bin/zterm -f fixed -e $SCI/bin/scilex $start_file $arguments &
        ;;

(I added the "-f fixed" option to zterm. zterm doesn't like that much, but scilab shows up anyways with some font... really really small for my screen, but better than the unreadable font for sure).

Any other suggestions?

C.[/QUOTE]
I gave up on the Ubuntu version and went to the Scilab home page and downloaded the binary and installed that which works perfectly.

[http://www.scilab.org/download/index_download.php?page=release.html](http://www.scilab.org/download/index_download.php?page=release.html)

It was much easier than fiddling with configuration files.

---

### Post by sawjew on 2005-10-10
[QUOTE=nsa_767]Hi, 

I know this isn't exactly a proper solution, but try and use maxima or octave instead of scilab until you've gotten things sorted....

Personally, I've never been able to figure scilab out.... But then, I have no matlab experience either.

Maxima is an excellent general purpose CAS, and Octave is extremely good with working with vectors... I also think Octave might have some (limited) matlab compatibility....

BTW: Someone should really start an area in the ubuntu forums for scientific apps and the like... If we all could get together, we might be able to get more of these apps (and up-to-date versions) into the repositories.

Not that I'm saying ubuntu is lacking in this area....[/QUOTE]
Yeah, I have Octave installed also and I think its probably more powerful than Scilab but I am GUI oriented and the only decent Octave Gui is Koctave which won't work properly on Gnome.

I think I'll just have to get used to Octave although I got Scilab working from their own binaries.

By the way, Octave does claim a high level of Matlab compatibility and I have been able to run many of my Matlab m files with little or no modification.

---

### Post by nsa_767 on 2005-10-10
Hi there,

You mentioned Koctave... Maybe you should consider installing KDE... Even though I normally work through Gnome, I have KDE installed... 

Anyway, I just installed Koctave, and it seems to run fine under Gnome (but of course it does need the KDE libraries).

Also, I know your not too interested in maxima (admittedly it is quite basic and limited compared to octave), but there are some good GUIs for it... My favourite is wxmaxima ([http://wxmaxima.sourceforge.net/)](http://wxmaxima.sourceforge.net/)), it makes everything point-and-click.

Oh, and note.... neither Koctave nor wxMaxima are in any of the ubuntu repositories...

---

### Post by jmooney on 2005-10-10
[QUOTE=nsa_767]Hi there,

You mentioned Koctave... Maybe you should consider installing KDE... Even though I normally work through Gnome, I have KDE installed... 

Anyway, I just installed Koctave, and it seems to run fine under Gnome (but of course it does need the KDE libraries).

Also, I know your not too interested in maxima (admittedly it is quite basic and limited compared to octave), but there are some good GUIs for it... My favourite is wxmaxima ([http://wxmaxima.sourceforge.net/)](http://wxmaxima.sourceforge.net/)), it makes everything point-and-click.

Oh, and note.... neither Koctave nor wxMaxima are in any of the ubuntu repositories...[/QUOTE]

You can also just install Octave, which is in the ubuntu repositories.  Additionally, if you have Emacs-X11 installed, you can start an inferior Octave process within it using the command {ALT-X} run-octave.

I've used both Octave and SciLab [and Matlab].  Between the two, I like Octave the best.

---

### Post by nsa_767 on 2005-10-10
sawjew said:
> 
I am GUI oriented and the only decent Octave Gui is Koctave


jmooney said:
> 
Additionally, if you have Emacs-X11 installed, you can start an inferior Octave process within it using the command {ALT-X} run-octave.


Thanks for that, always wanted to know how to run Octave from Emacs, but I don't think that really constitutes a GUI... Running it in Emacs is merely one step up from the console.... Not that Koctave is exactly point-and-click.

:) LOL, you guys have really made me want to learn Octave now! :) Unfortunately, I'm dropping maths end of this year... :cry:

---

### Post by Nekrataal on 2005-11-07
I got the same problem with the fonts, no one knows what to do to fix it?

---

### Post by sawjew on 2005-11-07
[QUOTE=Nekrataal]I got the same problem with the fonts, no one knows what to do to fix it?[/QUOTE]
I gave up on the Scilab version in the repositories and just installed the binary from the Scilab web site.  It was very easy to install and works perfectly.

---

### Post by rasty on 2007-07-07
HI everyone. I have kubuntu and use octave for scientific calcs. If someone installs koctave it forces to install octave 2.1 branch but afterwards you can point koctave to open octave 2.9.9(which i have installed separatelly). All this are allready in the repos (for kubuntu at least). Hope to have helped you! It works for me and other users too(that's how I learned about that trick, I tried to compile from source koctave but it excausted me really. Though I've compiled several kernels...).There is also Qtoctave (gnome users should check it if they don't want kdebase, libs etc.) but haven't tried it (yet...). Here is a link [URL="https://forja.rediris.es/projects/csl-qtoctave/"]

https://forja.rediris.es/projects/csl-qtoctave/[/URL]

---

### Post by Tinos on 2007-10-29
Hey, thanks for pointing me towards QtOctave. I gave kOctave a go (I'm on Kubuntu as well) but it seemed to crash whenever I close an m file! QtOctave looks really good though.  I was trying to use Scilab but it seemed pretty dodgy. You can't copy paste from the terminal, for instance.

---

### Post by fulgencio on 2007-11-12
Hi, 
Im interested in using scilab, I'm using Dapper Drake Ubuntu. So I followed your advice Downloaded scilab from its web page, and followed the instructions on the webpage. I think I installed correctly in my /home/user directory. The thing is, when I try to launch scilab with: bin/scilab, it gives me the following message:[PHP]root@magico-laptop:/home/magico/scilab-4.1.2# bin/scilab
/home/magico/scilab-4.1.2/bin/scilex: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory
[/PHP]

many thanks.

---

