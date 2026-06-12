---
title: "Problem with DosBox - cannot run dos program"
date: 2007-07-11
forum: General Help
---

### Post by lakestony on 2007-07-11
Hi there

I'm a fairly newbie to Ubuntu 7.04 which I have installed on an old HP Pavilion laptop OK

I want to run an old accounts dos package called CASHFLOW.

I followed the DOSBox instructions but got an error message after $ mkdir ~/dos/c in a regular terminal - 
it allowed $ mkdir ~/dos/

Eventually by exiting the terminal and going to the Home I gor a c Folder within the dos folder and then copied the Cashflow Folder into it (this contained the cashflow.exe as well as other items)

I can mount the c folder in dosbox as per istructions

It seems to accept chdir to cashflow folder but will not allow me to run cashflow - it keeps saying I must change to the cashflow folder first.

Anyone know where I am going wrong?

Cheers and TIA

Tony

---

### Post by MoLE on 2007-07-23
I'd be willing to bet that cashflow has a configuration file that has the full path to the program inside it - if you're just copying in a backup of the original install, you will either need to (a) duplicate the directory structure of the original install, or (b) install the app again in the dosbox environment you have created.

You might want to consider having a look at the cashflow documentation.

What is the specific error message that you get in dosbox when you try to run the program?

I assume you're doing something like:
```

z:\> c:
c:\> cd cashflow
c:\CASHFLOW> cashflow.exe

```

---

