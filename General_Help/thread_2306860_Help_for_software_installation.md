---
title: "Help for software installation"
date: 2015-12-19
forum: General Help
---

### Post by anna15 on 2015-12-19
Hi,
I'm a newborn linux user. I tried to install Adobe since I couldn't find any open sources software allowing to create notes and underlign option. Anyway, that's not my issue. 

So as a creat student, I followed advices given by ReadMe : 
 [QUOTE=ReadMe]To install Adobe Reader 9.1 using a .bin installer  1.   Open a terminal window.
  2.   Change directory (using the  cd  command) to the directory that contains the bin file.
  3.   Make sure that .bin installer has the execute permissions. If not then run
   chmod u+x AdbeRdr9.1.0-1_i486linux_enu.bin  
  4.   Run the following command:
   ./AdbeRdr9.1.0-1_i486linux_enu.bin  
 By default Adobe Reader is installed in /opt/Adobe. You can however,  specify a different location by using the following command-line option:  --install_path=  ** <dir path where you want to install>**  5.   Add  ** <reader_install_dir>**/bin to the PATH environment variable to allow browsers to launch Adobe Reader, where  ** <reader_install_dir>** is the installation directory of Adobe Reader 9.1. 

[/QUOTE]
It worked until the 4th point.  
that what came out when I run the .bin "program"
[QUOTE=My terminal]Extracting files, please wait. (This may take a while depending on the configuration of your machine)

This installation requires 136 MB of free disk space.

Enter installation directory for Adobe Reader 9.5.5 [/opt][/QUOTE] My problem is that I can't install it in /opt where it is suppose to go naturally. I checked, I've all rights on / so on /opt ... but I never managed to put anything in /opt via the terminal.

Then I tried to insert the install path straight in the same lign as the excecuting program as read in"read me" : 
[QUOTE=My terminal] /opt $ ~/Téléchargements/AdbeRdr9.5.5-1_i486linux_enu.bin --install_path=/opt

Extracting files, please wait. (This may take a while depending on the configuration of your machine)

This installation requires 136 MB of free disk space.
ERROR: Cannot write to directory "/opt".[/QUOTE] 
Is it a correct way to do it ?

Thanks for your help.
-A

---

### Post by The Cog on 2015-12-19
To write to directories outside of your home directory, you need extra permissions. You can gain these temporarily by preceding the command you want to run with the word sudo which then runs the command as user root (the super user). So the command would be:
```
sudo ./AdbeRdr9.1.0-1_i486linux_enu.bin
```

See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I don't understand what you want to use this program for. You say "create notes and underlign option". 
For creating notes, with underlines, bullet points etc., I would suggest using LibreOffice. LibreOffice is  a full featured office application and very probably already installed. If it is not already installed, this command will download and install it:
```
sudo apt-get install libreoffice
```

I could be wrong, but I thought that adobe reader was only a reader, and won't allow you to create documents at all.

---

### Post by ian-weisser on 2015-12-19
The supported recent versions of Adobe Reader (currently v11) do indeed add features like light highlighting, commenting, OCR, certificate-based signatures, etc. I use them regularly...on Windows.

Adobe abandoned support for it's previous Linux version of Acrobat Reader several years ago.
I recommend against using Reader 9 - it is obsolete, and vulnerable to known exploits. Adobe has abandoned it, and will not fix those vulnerabilities.
The features you want to use may (or may not) be in Reader 9. They may (or may not) work.
Reader 9 may (or may not) crash immediately with your version of Ubuntu.

As already discussed, most Linux users use LibreOffice for various PDF manipulations, and other non-Adobe PDF readers. However, that does not mean they are compatible with your workflow. Adobe makes money selling PDF-creating software, and is not interested in helping open-source tools to be more compatible.

You have chosen a task (manually installing unsupported software) that usually requires patience and a certain level of Linux skill and experience.
It's difficult. Even experts sometimes fail at that task.
Have a plan for how you will do your workflow if Ubuntu + Reader does not work.

---

### Post by Sweet_Baby_Jamie on 2015-12-20
I use [Xournal]("http://xournal.sourceforge.net") at school for note taking.  It also annotates PDFs, including highlighting, underlining and filling in the blanks.  It's in the Ubuntu repositories too, so you can install using the Software Center or Synaptic.

---

### Post by anna15 on 2015-12-21
Thanks for your help and advice. 

I check Libreoffice and the pdf format is completely messed up. Adobe 9.5 (that I finaly managed to install), the newest version of Reader for Linux doesn't have the function I was looking for. I therefor tried Xournal. I had some trouble, conflict between my linux version and the software. 
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
sudo apt-get install xournal       that I managed to extract to /opt
And diiiim ! It worked ! And it will do the job. 

Thanks Jamie for the recommendation.

---

