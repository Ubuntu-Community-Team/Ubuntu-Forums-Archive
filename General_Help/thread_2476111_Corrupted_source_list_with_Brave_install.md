---
title: "Corrupted source list with Brave install?"
date: 2022-06-16
forum: General Help
---

### Post by alvinmoneypit on 2022-06-16
Yesterday I installed Brave on my Ubuntu 18.04 system.  I get the message:
> E: Type '&#8220;deb' is not known on line 1 in source list /etc/apt/sources.list.d/brave-browser-release.list


I looked at the file and found it had a quotation mark at the beginning.  From other post, I noted  they instruct to remove this to repair the file.  The system gives me root privilege but still does not allow to edit this file saying "no write permissions for this file". 
So just wondering how to proceed.  Thanks for all replies.

---

### Post by grahammechanical on 2022-06-16
I suggest not editing the sources.list.d file but checking the how you installed the Brave browser. From where? What commands did you use? Did you install it through Ubuntu Software (20.04)? That application has a snap version of Brave browser.

Regards

---

### Post by ActionParsnip on 2022-06-16
What is the output of:
```

cat -n /etc/apt/sources.list.d/brave-browser-release.list

```
Thanks

---

### Post by alvinmoneypit on 2022-06-16
Here is the output of the requested query:
>    1	&#8220;deb [arch=amd64] [https://brave-browser-apt-release.s3.brave.com/](https://brave-browser-apt-release.s3.brave.com/) stable main&#8221;

I am running ubuntu 18.  I downloaded Brave through the command line.

---

### Post by #&amp;thj^% on 2022-06-16
The instructions OP used are here: [https://brave.com/linux/](https://brave.com/linux/)

---

### Post by alvinmoneypit on 2022-06-16
No, I did not use those instructions, 1fallen.  I did find it on the web.  I'll try to find it again and post.

---

### Post by #&amp;thj^% on 2022-06-16
> **alvinmoneypit said:**
> No, I did not use those instructions, 1fallen.  I did find it on the web.  I'll try to find it again and post.

Thanks for the correction, and the link followed would be a bonus. ;)

---

### Post by alvinmoneypit on 2022-06-16
sorry, I cannot figure out where and how I installed.  Looking at firefox history does not help.  I may have gotten it from the software center gui.  Shortly after, I noticed I have no access to gnome control center and it cannot be found anywhere I look.  I have the red icon next to online status says, "an error occurred, please run package manager from the right click menu or apt-get in a terminal to see what is wrong" and then refers to this file.

---

### Post by alvinmoneypit on 2022-06-16
I most likely used this command, but am not absolutely sure.
> sudo apt install -y brave-browser

---

### Post by #&amp;thj^% on 2022-06-16
> **alvinmoneypit said:**
> I most likely used this command, but am not absolutely sure.

Not sure that would work, without an edit to your sources.
It draws from this source:
```
&#8220;deb [arch=amd64] https://brave-browser-apt-release.s3.brave.com/ stable main&#8221; 
```

---

### Post by ActionParsnip on 2022-06-16
Edit the file and remove the quotation marks

---

### Post by ActionParsnip on 2022-06-16
I also assume you mean Ubuntu 18.04. There is no "Ubuntu 18". It's not a thing and has never been a thing

---

### Post by #&amp;thj^% on 2022-06-16
> **ActionParsnip said:**
> Edit the file and remove the quotation marks

+1
or just run:
```
 echo "deb [arch=amd64] https://brave-browser-apt-release.s3.brave.com/ stable main" | sudo tee /etc/apt/sources.list.d/brave-browser-release.list
```
wouldn't hurt to see this as well:
```
cat /etc/apt/sources.list.d/brave-browser-release.list
```
after adding it.

---

### Post by alvinmoneypit on 2022-06-16
yes, 1fallen, that looks familiar as well.  I may have tried the above and then simply got it from the GUI software center.  It shows it is installed, but trying to remove it fails with no error message.

---

### Post by #&amp;thj^% on 2022-06-16
> **alvinmoneypit said:**
> yes, 1fallen, that looks familiar as well.  I may have tried the above and then simply got it from the GUI software center.  It shows it is installed, but trying to remove it fails with no error message.
Sounds as if a broken install, to try and help let's do it their way:
```
sudo apt install apt-transport-https curl
```
and:
```
curl -s https://brave-browser-apt-release.s3.brave.com/brave-core.asc | sudo apt-key --keyring /etc/apt/trusted.gpg.d/brave-browser-release.gpg add -
```
and:
```
echo "deb [arch=amd64] https://brave-browser-apt-release.s3.brave.com/ stable main" | sudo tee /etc/apt/sources.list.d/brave-browser-release.list

```
now update
```
sudo apt update
```
show any errors if any before going to installing.

---

### Post by alvinmoneypit on 2022-06-16
The command 
> sudo apt install apt-transport-https curl
errors out with:
> E: Type '&#8220;deb' is not known on line 1 in source list /etc/apt/sources.list.d/brave-browser-release.list
E: The list of sources could not be read..
Terminal posted the reply twice on the one input.

---

### Post by deadflowr on 2022-06-16
Run the 3rd command 1fallen posted first, which should fix the error issue.
(The echo blah blah blah command)

---

### Post by alvinmoneypit on 2022-06-16
thanks, deadflwr, things are working again.  Shall I continue with the installation?

---

### Post by #&amp;thj^% on 2022-06-16
just update and upgrade via terminal 
and show any more errors if any.

---

### Post by alvinmoneypit on 2022-06-16
the only thing that came up is:
> E: The repository 'cdrom://Ubuntu 18.04.2 LTS _Bionic Beaver_ - Release amd64 (20190210) bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

Not sure what  cdrom file I could have corrupted.  Last week I was using the dvd drive, but Its not everyday or every week I use it.

---

### Post by #&amp;thj^% on 2022-06-16
> **alvinmoneypit said:**
> the only thing that came up is:

Not sure what  cdrom file I could have corrupted.  Last week I was using the dvd drive, but Its not everyday or every week I use it.

just disable them, with your software center sources/list.
that's odd you haven't seen it before now..?

---

### Post by alvinmoneypit on 2022-06-16
Thanks, 1Fallen.  I don't use the command line much, nor add many programs.  Last week I did use it to copy a dvd to see if it would work.  I'll mark the thread solved, if that is still a thing.

---

### Post by #&amp;thj^% on 2022-06-16
Whoops don't misunderstand me, this will have no effect on your CD/DVD drive:
those were just repo/sources that came with the install media used...if needed.

---

### Post by alvinmoneypit on 2022-06-16
I kind of understand, I'll try to restate.  So my cdrom is banned as a source for updates, correct?

---

### Post by #&amp;thj^% on 2022-06-16
Not unless you un-checked, disabled it just now. And you also can use USB drive if ever needed for a source.
18.04 is an older in comparison  to focal and jammy therefor no signature **so you will see that in the terminal when used for updates or installs**.
it shouldn't have any bad effect to your system, except that error/warning that you seen now.
see screenshot:

---

### Post by ajgreeny on 2022-06-16
The line for the cdrom should normally be commented out in the /etc/apt/sources.list file, with a # as the first character, and therefore ignored by the system when updating.
For some reason that is not so in your system so you need to open that file as root and add the # manually.

---

### Post by alvinmoneypit on 2022-06-16
thanks everyone!

---

