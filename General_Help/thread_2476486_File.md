---
title: "File"
date: 2022-06-27
forum: General Help
---

### Post by 7HMSP7bt on 2022-06-27
Hello , I have a file , maybe an application that I have to open it on ubuntu , but I don't know how , it does not open .

I have to prepare a short report that describes the vulnerabilities of the attached application. The application is used by system administrators (i.e. root users) to check the strength of passwords on a system they manage.

For the purposes of this challenge, the application makes some very simple checks (whether a user has a password which is the same as his/her username, whether the password is the username plus '1234' or '!@#$' patterns and finally, whether the password is a 4-digit number).

For testing purposes candidates are instructed to use a 64-bit Ubuntu 18.04.1 distribution (although other distributions may also meet the runtime library requirements).

So I have a file named **pwv** , but it shows as a file only . How am I supposed to open that file or to run that file as an application . I tried to run it but nothing happens .

Any ideas ?

---

### Post by QIII on 2022-06-27
Moved to General Help.

The Forum Feedback & Help section has the following tag line at the top:  > Forum Feedback and Help is not for general support enquiries

That forum is to request help with the forum software or its behavior.

Note: although we will help you with the technical issue of running the application or opening the file, we do not provide help for homework, job interviews and the like.

---

### Post by The Cog on 2022-06-27
You could try to find out what kind of file it is with the command
```
file pwv
```
When you say you want to "open" the file, do you mean you want to open it for editing, or you want to execute it? To execute it. you need to set the executable flag with this command:
```
chmod +x pwv
```

---

### Post by 7HMSP7bt on 2022-06-27
So , i tried it and this is my result

---

### Post by grahammechanical on 2022-06-27
If you do not know what that file does then do not run it as an application. You have been told that it has security vulnerabilities. So, why are you putting your machine at risk by running it?

Open the file manager and select that file and then right click the file and select Properties and read what the file manager says about that file. It may be that the file is a kind of application called script in Linux. If it is a script then it will be an executable text file and text files can be opened in a text editor such as Gedit. That will allow you to study the code that makes up the script.

Now, it is up to you to identify the vulnerabilities and work out the code to modify the script so as to fix the vulnerabilities. You should have been told all this.

Regards

---

### Post by 7HMSP7bt on 2022-06-27
This is what I see [IMG]https://ubuntuforums.org/attachment.php?attachmentid=290661&stc=1[/IMG]

---

### Post by 7HMSP7bt on 2022-06-27
I guess I found what it does , so now I have to do this :

[FONT=Arial]The application security assessment report must describe for each vulnerability:[/FONT]
[FONT=Arial]a) the technical description of the vulnerability ("what is it?", "where in the binary is it?", "how can one trigger the vulnerability?") b) the impact of the vulnerability ("what can an attacker gain through exploitation?", "how does the vulnerability affect the system and its users?")[/FONT]
[FONT=Arial]c) a recommendation to the developers of the application ("what should be done to mitigate the vulnerability").[/FONT]

---

### Post by QIII on 2022-06-27
And that work is for you to do, not for the community to do for you.

Closed.

---

