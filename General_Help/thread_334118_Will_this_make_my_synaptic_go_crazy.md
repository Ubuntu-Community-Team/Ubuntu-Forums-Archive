---
title: "Will this make my synaptic go crazy?"
date: 2007-01-08
forum: General Help
---

### Post by Nonno Bassotto on 2007-01-08
Don't care about the actual name of the packages if you don't know. The point here is the install procedure, so just think of them as packages x, y, z...

I'm currently using TeTeX, but I'd like to change to TeXlive. The problem is that I'm also using the package Asymptote. This should be installable both on top of TeTeX or on top of TeXlive, but there is some bug that makes it depend only on TeTeX.

I found the following workaround.

If install TeXlive, synaptic forces me to remove TeTeX (correct), but also to remove Asymptote. Now if I mark Asymptote for a reinstall, Synaptic accepts it, but wants to remove Rubber. Finally I mark Rubber for reinstall and Synaptic asks me to mark TeXlive for install (which I already did). At this point the selection of packages is correct.

Do you think that this procedure will cause me problems when I install other packages or upgrade?

---

### Post by az on 2007-01-08
Using the command-line, this is exactly what the -s switch in apt-get is for.

Can you elaborate about the bug in Asymptote?  Is the bug that the dependencies are not correct or is it something else?  Because both tetex and texlive provide latex.  Latex is not a real package but a dependency that both of those satisfy.

---

### Post by Nonno Bassotto on 2007-01-08
The bug (at least I think it is) is that Asymptote depends explicitly on tetex-extra, while it should be usable on top of any working latex installation.

I don't understand how the -s option can help. I can simulate what happens doing this, but then I'm not sure that everything will work right, for example when upgrading to Fiesty or when installing another related package. I have no idea, because I don't know how apt-get works, so I asked here. If I have a package installed without a dependency (it seems that I can achieve this by the tortous way I described) can this cause issues (apart from the package not working, but I'm quite sure it will)?

Moreover in the command line I don't know how to reproduce the steps I described (install texlive while reinstalling asymptote and rubber). I tried
```

sudo apt-get -s --reinstall install texlive asymptote rubber

```
but it just failed saying
```

Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso       
Reading state information... Fatto               
Alcuni pacchetti non possono essere installati. Questo può voler
dire che è stata richiesta una situazione impossibile oppure, se
si sta usando la distribuzione "unstable", che alcuni pacchetti
richiesti non sono ancora stati creati o rimossi da incoming.
Le seguenti informazioni possono aiutare a risolvere la situazione: 

I seguenti pacchetti hanno dipendenze non soddisfatte:
  asymptote: Dipende: tetex-bin ma non sta per essere installato oppure
                      latex ma non è installabile
             Dipende: tetex-bin ma non sta per essere installato oppure
                      dvips ma non è installabile
             Dipende: tetex-extra ma non sta per essere installato
  rubber: Dipende: tetex-bin ma non sta per essere installato oppure
                   texlive-latex-base ma non sta per essere installato
  texlive: Dipende: texlive-latex-recommended ma non sta per essere installato
           Dipende: texlive-context ma non sta per essere installato
E: Pacchetto non integro


```

Ok, probably you don't speak italian, but it doens't say anything which is not obvious. It seems different from the situation I was able to reproduce in synaptic.

---

### Post by az on 2007-01-08
> **Nonno Bassotto said:**
> The bug (at least I think it is) is that Asymptote depends explicitly on tetex-extra, while it should be usable on top of any working latex installation..


[http://packages.ubuntu.com/edgy/tex/asymptote](http://packages.ubuntu.com/edgy/tex/asymptote)

I see what you mean - it requires tetex-bin *or* latex, but also requires tetex-extra which requires tetx-bin.
> **Nonno Bassotto said:**
> 
I don't understand how the -s option can help. I can simulate what happens doing this, but then I'm not sure that everything will work right, for example when upgrading to Fiesty or when installing another related package. I have no idea, because I don't know how apt-get works, so I asked here. If I have a package installed without a dependency (it seems that I can achieve this by the tortous way I described) can this cause issues (apart from the package not working, but I'm quite sure it will)?..

Running an apt-get -s simulation will let you know exactly what packages will get installed and which ones will get removed.  I have a feeling that doing it the way you descrive with Synaptic will end up removing some packages.

> **Nonno Bassotto said:**
> 
Moreover in the command line I don't know how to reproduce the steps I described (install texlive while reinstalling asymptote and rubber). .

That's the thing:  you cant.  Neither can Synaptic.  Are you sure it's not unmarking some packages without you knowing about it?

---

### Post by Nonno Bassotto on 2007-01-08
The following is the list of packages to be removed
```

latex-beamer
latex-ucs
latex-xcolor
pgf
tetex-base
tetex-bin
tetex-extra

```
The following is the list of packages to be installed
```

perl-tk (versione 1:804.027-5)
texlive-base (versione 2005.dfsg.1-1)
texlive-base-bin (versione 2005.dfsg.1-1ubuntu3)
texlive-common (versione 2005.dfsg.1-1)
texlive-doc-base (versione 2005-2)
texlive-doc-en (versione 2005-2)
texlive-latex-base (versione 2005.dfsg.1-1)
texlive-pdfetex (versione 2005.dfsg.1-1ubuntu3)

```
Finally this is the list of packages to be reinstalled
```

asymptote (versione 1.03-1)
rubber (versione 1.1-2)

```

So it seems it would do what I expect. Anyway I'm getting the feeling that this is not a very safe operation. Maybe I will try to install asymptote from source. I'll open a bug in launchpad, hoping it will be fixed for fiesty.

---

