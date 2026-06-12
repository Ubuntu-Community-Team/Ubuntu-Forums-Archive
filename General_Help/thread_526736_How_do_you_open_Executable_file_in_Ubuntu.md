---
title: "How do you open Executable file in Ubuntu?"
date: 2007-08-15
forum: General Help
---

### Post by UK-Wobbie on 2007-08-15
Do any one no how to open a executable file in Ubuntu? Or is there any code or tools out there what will do this job? 

Thanks :)

---

### Post by HermanAB on 2007-08-15
What do you mean?

You can look at any file with a hex editor, or print all text in the file using 'strings':
$ strings filename

---

### Post by UK-Wobbie on 2007-08-15
> **HermanAB said:**
> What do you mean?

You can look at any file with a hex editor, or print all text in the file using 'strings':
$ strings filename

I mean when i click on it! It will not open... All it says is this 

Cannot open /home/.........../Desktop/untitl...older/epsxe - for linux/epsxe: No application suitable for automatic installation is available for handling this kind of file.

I wanna open this file! I have got ubuntu 6.2 or something like that on one of my old computers... I do not use it alot! 
And it works on that :( Now i have got the new Ubuntu on one of my new computers and ever executable file will not open.


Am sorry i did not put down what Executable file it is! It's a data file what is a ps1 and n64 emu :)

---

### Post by ramjet_1953 on 2007-08-15
If you mean an Windows executable like "myfile.exe", of course you can't open it under Linux natively.

Just like you can't open Mac OSX files under Windows.

However, you can always install wine and see if the application will install and run under this compatibility layer.

Another option is to install a virtualization package, like VirtualBox, or VMWare.

However, if you are talking about Python executables, or shell scripts, come back with more details of the fie and we can help.

Regards,
Roger :cool:

---

### Post by UK-Wobbie on 2007-08-16
> **ramjet_1953 said:**
> If you mean an Windows executable like "myfile.exe", of course you can't open it under Linux natively.

Just like you can't open Mac OSX files under Windows.

However, you can always install wine and see if the application will install and run under this compatibility layer.

Another option is to install a virtualization package, like VirtualBox, or VMWare.

However, if you are talking about Python executables, or shell scripts, come back with more details of the fie and we can help.

Regards,
Roger :cool:

Hey dude thanks for your help.
I say it is a Windows executable file! I got it from some Game emu Website.. 

I have had a go on Using Wine and that did not do anything lol
I no there is some code what will yet me run the executable file! I got something on my old Ubuntu computer what i do not no or it may be made it to it! I use this executable file on that and It opens ok :( Saying that lol Be for where back now be for i restarted restilling Ubuntu on to my New computer it worked!!! I do not no if it may be the Wines V :confused: I got Wine 0.9.40 instilled... It's the only Wine i like lol Some Wines do not work on some of my games! But that Wine works ok on all. 

It's makeing me mad :( It use to open way back lol And now it keep saying 

Cannot open /home/......./Desktop/untitl...older/epsxe - for linux/epsxe: No application suitable for automatic installation is available for handling this kind of file.

I used Wine did not work, I used Some tool did not work lol I need some code or something what can run the executable file! 
I do not no if it is a Windows or Linux executable file! 
I say more to Windows.. I have got some Emu on my Windows Computer! But i did not use any of them.. I did not no if it will work lol So i got some Emu from some game website.

Thanks :)
P.s Emu means Emulator :)

---

### Post by heimo on 2007-08-16
> **UK-Wobbie said:**
> I do not no if it is a Windows or Linux executable file!

I'll give just one tip, can't help with you the rest. You can get information about the file by running command *file *on it. Let's say the binary is /bin/ls, you'd run:
```
file /bin/ls
```

And it'll tell you what kind of file it is.

---

### Post by UK-Wobbie on 2007-08-16
> **heimo said:**
> I'll give just one tip, can't help with you the rest. You can get information about the file by running command *file *on it. Let's say the binary is /bin/ls, you'd run:
```
file /bin/ls
```

And it'll tell you what kind of file it is.

Cool where do i put this lol In Terminal?

I been playing about on some file i made out of flash lol They are DOS/Windows executable and they open and run ok! 
But i looked at the Emulator executable file it says in the properties!

Type: executable

Then 

MIME type: application/x-executable

What do that mean? lol

The executable i made work ok! But the executable i got from some website do not work at all :(??

Thanks

---

### Post by heimo on 2007-08-16
> **UK-Wobbie said:**
> Cool where do i put this lol In Terminal?

Yes, you can run that in terminal.

---

### Post by UK-Wobbie on 2007-08-16
> **heimo said:**
> Yes, you can run that in terminal.

Am sorry to be a b lol But how do i use this code?

Like file /desktop/then game.exe?

Thanks :)

---

### Post by heimo on 2007-08-16
> **UK-Wobbie said:**
> Am sorry to be a b lol But how do i use this code?

Like file /desktop/then game.exe?

Thanks :)

If the file is game.exe, there's no doubt it's Windows executable, so there's no point of running file command on it. It'll just tell you what you already know. You should perhaps search for instruction on using Wine and running games on it. Or get cedega. You may get better instructions on game related subforum here on Ubuntuforums.

---

### Post by UK-Wobbie on 2007-08-16
> **heimo said:**
> If the file is game.exe, there's no doubt it's Windows executable, so there's no point of running file command on it. It'll just tell you what you already know. You should perhaps search for instruction on using Wine and running games on it. Or get cedega. You may get better instructions on game related subforum here on Ubuntuforums.

Well i do not no if it is a exe file! But all it says is the emu name and in properties it says executable! And then application/x-executable :confused:

I have made some executable files on swishmax! And they open ok... I may have got the right pluggings to do the job :razz: And when i made it it says the file name then .exe and in the properties it says DOS/Windows executable then application/x-ms-dos-executable and that works ok! 

So i am sorry if i do not no what to do! 
And if you do not no what i am saying lol :)

I am like you here i do not no what the 2 files are!!! All i no they are executable files.. But have you got more then one executable type? Or something :(

Thanks for your help and i will keep looking on this file type :)

---

