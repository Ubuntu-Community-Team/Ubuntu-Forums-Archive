---
title: "I can't format texts in an email editor or a browser address bar. They disappear"
date: 2020-09-18
forum: General Help
---

### Post by linuxrite on 2020-09-18
Ubuntu: 1804
I installed Ubuntu in December 2018 after Windows 10 destroyed my hard disk.
I rarely encounter serious errors. _But_ **one** ***problem*** *is* _**persistent and random**_. As you can see I could format texts here. But if I format texts in an email editor or even some other editors provided by other websites, after I double click on texts to select them, they immediately disappear as if **double click means delete**, or if I use mouse left button and the cursor to select the texts, the texts disappear after I click on any type of format.

I couldn't format the texts.
It happens frequently and randomly.
It happens either I use Firefox or Chrome browser. (It happens only to browsers, never software like LibreOffice.) 

It has been about a year. 
I have uninstalled both Firefox and Chrome and reinstalled. It doesn't help.
I searched in this forum and on the Internet, but no luck.   

Does anyone know how to fix?

---

### Post by sudodus on 2020-09-18
It sounds like something I have never encountered.

Have you installed the 'restricted extras'? That package brings among other things a set of fonts, that may be necessary to render the formatting of the text.

```

sudo apt update
sudo apt install ubuntu-restricted-extras

```

Otherwise there could be problems in the cooperation between the browser and the web page, where you try to do the formatting. In that case we can't do much in Ubuntu.

---

### Post by Impavidus on 2020-09-18
Have you tried disabling browser extensions? Have you tried running the browser with a fresh profile?

---

### Post by TheFu on 2020-09-18
Just guessing, but have you tried a different mouse or tweaking the mount settings to speed up or slow down what a double-click means?  My mom had terrible arthritis and her mousing became a problem. She had issues with select + drag + drop too. She was always accidentally releasing the mouse while dragging stuff.

As for the browser stuff, I'd create a new userid, logout, login using the new userid and see if the problems persist.  
If they don't, then the problem is with your browser settings for the other userid.  
If they do, then it is a system-wide issue.  
If system-wide, I'd create and boot from a "Try Ubuntu" flash drive and test again. Perhaps try a different DE.
If the issues continue after that, then it is either hardware or your ISP.

As always, 
[LIST=1]
[*]Simplify
[*]Test
[*]Repeat from step 1 until the problem has been simplified to become known.
[/LIST]

---

### Post by SeijiSensei on 2020-09-18
I don't know how to fix the problem, but I do know something that would help if you use Firefox. It's a browser extension called Textarea Cache. It records everything you type into a browser window so you can recover from accidentally deleting what you've written. You can scroll back through previous entries as well. I write a lot on forums, and Textarea Cache is a must-have extension for me.

---

### Post by linuxrite on 2020-09-21
It took me a while to find my own question. The one-account-for-all-forums is a bit confusing.  Thank all of you for your help   > **sudodus said:**
> Have you installed the 'restricted extras'?    I will try it. But when I double clicked texts here, they didn't disappear. I'm using Firefox with some extensions.  > **Impavidus said:**
> Have you tried disabling browser extensions? Have you tried running the browser with a fresh profile? Good questions. It's possible one of the extensions is the culprit.   > **TheFu said:**
> Just guessing, but have you tried a different mouse or tweaking the mount settings to speed up or slow down what a double-click means? ...  If they do, then it is a system-wide issue.     I mostly use the touchpad. But they do. I can format texts when I use any other software. It only happens to the browsers.  > **SeijiSensei said:**
>  It's a browser extension called Textarea Cache.  I can get the texts back by pressing ctrl+z. The problem is I am unable to format the texts when I use browsers. It seems like formatting texts = deleting them, sometimes selecting texts = deleting them.

---

### Post by linuxrite on 2020-09-21
What makes it more mysterious is the fact that it happens RANDOMLY. Sometimes, I can select texts and format. At first, it only happened to Chrome browser, then "spread" to Firefox. Now it still happens more frequently to Chrome than Firefox.

---

### Post by TheFu on 2020-09-21
> **TheFu said:**
>  
As for the browser stuff, I'd create a new userid, logout, login using the new userid and see if the problems persist.  
If they don't, then the problem is with your browser settings for the other userid.  
If they do, then it is a system-wide issue.  
If system-wide, I'd create and boot from a "Try Ubuntu" flash drive and test again. Perhaps try a different DE.
If the issues continue after that, then it is either hardware or your ISP.

As always, 
[LIST=1]
[*]Simplify
[*]Test
[*]Repeat from step 1 until the problem has been simplified to become known.
[/LIST]

Dd you do these?  Linux is multiuser. Take advantage of that.

---

### Post by linuxrite on 2020-09-21
> **TheFu said:**
> Dd you do these?  Linux is multiuser. Take advantage of that. Sorry, I misunderstood your first reply here. I thought you meant the browser userid.  I then tried to create a ubuntu new ID to test, but failed to create one.

---

### Post by ajgreeny on 2020-09-21
Failed to create a new user in what way? What did you do to try and create one?

---

### Post by linuxrite on 2020-09-21
> **ajgreeny said:**
> Failed to create a new user in what way? What did you do to try and create one?  I followed this tutorial: [https://www.digitalocean.com/community/tutorials/how-to-add-and-delete-users-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-add-and-delete-users-on-ubuntu-18-04) After   sudo adduser newuser  I was asked to assign a password for the new user. But I always got "wrong password" error. I tried both simple passwords and long strong passwords.

---

### Post by Impavidus on 2020-09-21
First sudo asks for your own password before it will run adduser as root. Then adduser will ask for the password of the new user.

BTW, better to copy terminal output to your post as text, not as screenshot. And include the command, not just the output.

---

### Post by CelticWarrior on 2020-09-21
And although it's perfectly fine and laudable to do it with commands, all of that can be easily done graphically in system settings > users.

No doubt you learned a valuable skill in your research but sometimes there's really no need to complicate things that were made obscenely SIMPLE a long time ago.

---

### Post by linuxrite on 2020-09-21
> **Impavidus said:**
> First sudo asks for your own password before  it will run adduser as root. Then adduser will ask for the password of  the new user.

BTW, better to copy terminal output to your post as text, not as  screenshot. And include the command, not just the output.

> **CelticWarrior said:**
> And although it's perfectly fine and laudable to do it with commands, all of that can be easily done graphically in system settings > users.

No doubt you learned a valuable skill in your research but sometimes there's really no need to complicate things that were made obscenely SIMPLE a long time ago.

**Thank both of you!** *Both helped me* _successfully create_ [COLOR=#0000ff]new users.[/COLOR] 
I then logged in with one of the new users and logged in my email account, forums, etc. to test. I didn't add all of the extensions I used as the other user. I didn't encounter the problem. But the problem is random. 

[COLOR=#006400] I can always format texts here. [/COLOR]

When I wrote my last post here, I also wrote two emails. I could format one email without the problem and then encountered the problem when I edited the other.

---

