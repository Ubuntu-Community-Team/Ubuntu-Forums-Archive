---
title: "Cannot get a PDF Printer to work"
date: 2007-04-01
forum: General Help
---

### Post by jado316 on 2007-04-01
Hi ppl,

I'm new at these forums and at Ubuntu. I've got 6.06 (Dapper Drake) installed on a Virtual PC using Microsoft Virtual PC 2004. My host OS is Windows XP Home. I'm trying to get a PDF printer (using this cups-pdf thing) installed. I'm following the tutorial at [this thread]("http://www.ubuntuforums.org/showthread.php?t=188860"). Now, I know this is probably a bit pathetic, but I'm stuck on the first step where I have to install cups-pdf. I have used the command 'sudo apt-get install cups-pdf' at the Terminal to try to install cups-pdf but it didn't work. I would like to know where to get cups-pdf and how to install it. 'Cups-pdf for dummies' instructions would be useful because I know virtually nothing about installing apps using the terminal (even though I somehow got Adobe Flash Player installed).:confused: 

Thanks

---

### Post by nanotube on 2007-04-01
cups-pdf is in the universe repository. you need to enable that first (in synaptic, go to repositories)
that's my guess for what's up. since you didn't provide the actual error message, i can't be sure why it "didn't work". :)

---

### Post by jado316 on 2007-04-01
There's no cups-pdf in the Synaptic Package Manager Repository. I have attached a screenshot of the error message in the terminal window when I try to install cups-pdf with the 'sudo apt-get install cups-pdf' command.

---

### Post by jado316 on 2007-04-01
Another thing, I'm wondering If I'm trying to install cups-pdf the wrong way. On a website I found in a Google search it says

> 
Install cups-pdf by using:
$sudo apt-get install cups-pdf

When they say 'by using' do they mean open terminal and enter the command shown, or is is something else like a Run dialog similar to Windows'

---

### Post by jado316 on 2007-04-01
Yay!:-D I got it to work. I just had to download and install cups-pdf from [here]("http://packages.debian.org/stable/graphics/cups-pdf") in a .deb file.

---

### Post by bmt on 2007-04-01
It's generally better to use Ubuntu's repositories as a first choice as packages from other sources may have slight differences -- sometimes significant, though usually okay.

If you start the Synaptic Package Manager and go to the menu Settings -> Repositories, you have the option to tick the box for other Ubuntu repositories, which are not set by default. Click close to close the dialogue and then menu Edit -> Reload Package Information.

You now have a more comprehensive list of packages available.  (There are several other ways of achieving the same result.)

---

### Post by nanotube on 2007-04-01
> **jado316 said:**
> There's no cups-pdf in the Synaptic Package Manager Repository. I have attached a screenshot of the error message in the terminal window when I try to install cups-pdf with the 'sudo apt-get install cups-pdf' command.

that error you post looks like you maybe had synaptic running while you were trying to use apt-get? you can only use one package manager at a time, so as not to screw up the directory, that's why they lock it. 

bmt is right, you are generally better off using the repos, if you can. but i guess you can let this be a lesson for the future. :)

try opening synaptic, adding the repository as bmt and i said, click update, then find cups-pdf. (or if you prefer to use apt-get, /close/ synaptic after adding repositories, /then/ try the apt-get).

---

