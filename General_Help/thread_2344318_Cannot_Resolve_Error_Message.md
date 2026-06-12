---
title: "Cannot Resolve Error Message"
date: 2016-11-24
forum: General Help
---

### Post by daniell59 on 2016-11-24
Update information

Failure to download extra data files

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

pepflashplugin-installer

The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.

I would appreciate any help in resolving this error message.

Ubuntu 14.04 32

Thanks

---

### Post by howefield on 2016-11-24
Do you have any files present in /var/lib/update-notifier/user.d/

```
ls /var/lib/update-notifier/user.d/
```

---

### Post by slickymaster on 2016-11-24
> **daniell59 said:**
> Update information

Failure to download extra data files

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

[COLOR="#FF0000"]**pepflashplugin-installer**[/COLOR]

The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.

I would appreciate any help in resolving this error message.

Ubuntu 14.04 32

Thanks
Are you using [this PPA]("https://launchpad.net/~skunk/+archive/ubuntu/pepper-flash")? Any reason for not using the one in the repositories?

---

### Post by daniell59 on 2016-11-24
> **howefield said:**
> Do you have any files present in /var/lib/update-notifier/user.d/

```
ls /var/lib/update-notifier/user.d/
```

Please excuse my ignorance. How do I check to see if there are any files in the update notifier?

---

### Post by howefield on 2016-11-24
> **daniell59 said:**
> Please excuse my ignorance. How do I check to see if there are any files in the update notifier?

Possibly the output of the aforementioned terminal command

```
ls /var/lib/update-notifier/user.d/
```

will tell you.

---

### Post by daniell59 on 2016-11-24
> **howefield said:**
> Possibly the output of the aforementioned terminal command

```
ls /var/lib/update-notifier/user.d/
```

will tell you.

This is the result of the command.  data-downloads-failed

---

### Post by howefield on 2016-11-24
> **daniell59 said:**
> This is the result of the command.  data-downloads-failed

I'd suggest removing it, or at least moving it elsewhere so that you still have it if needed.

```
sudo mv /var/lib/update-notifier/user.d/data-downloads-failed ~/Documents
```

That will save a copy of the file in your Documents folder.

I'd also recommend using the adobe-flashplugin package from the Partners repository for your flash needs.

---

### Post by daniell59 on 2016-11-24
> **howefield said:**
> I'd suggest removing it, or at least moving it elsewhere so that you still have it if needed.

```
sudo mv /var/lib/update-notifier/user.d/data-downloads-failed ~/Documents
```

That will save a copy of the file in your Documents folder.

I'd also recommend using the adobe-flashplugin package from the Partners repository for your flash needs.

Thanks for your assistance. As of this post, the error message has not returned. I will give it several hours before marking the thread as solved.

---

### Post by daniell59 on 2016-11-25
I really hate to say it, but the problem is back.

---

### Post by daniell59 on 2016-12-18
Failure to download extra data files

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

pepflashplugin-installer

The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.

In spite of numerous attempts I have yet to resolve this problem. I tried many suggestions from people on this forum. I also googled and the solutions found did not work for me. I guess that I have two options. Live with it, reinstall the OS. I hope there is a third option.

Thanks in advance 

Ubuntu 14.04 32

---

### Post by howefield on 2016-12-18
Duplicate threads merged.

---

### Post by howefield on 2016-12-18
As far as I know the recommended method is to enable the Canonical "partner" repository and install the *adobe-flashplugin* package rather than use pepperflash.

I'd suggest purging the pepflashplugin-installer with..

```
sudo apt-get purge pepflashplugin-installer
```

then enable the Partners repository via the *Other Software* tab in the *Software & Updates* application and install flash with..

```
sudo apt-get install adobe-flashplugin
```

---

### Post by daniell59 on 2016-12-18
> **howefield said:**
> As far as I know the recommended method is to enable the Canonical "partner" repository and install the *adobe-flashplugin* package rather than use pepperflash.

I'd suggest purging the pepflashplugin-installer with..

```
sudo apt-get purge pepflashplugin-installer
```

then enable the Partners repository via the *Other Software* tab in the *Software & Updates* application and install flash with..

```
sudo apt-get install adobe-flashplugin
```

Can you please expand upon the following. Enable Canonical partner repository  also  enable the Partners repository via the *Other Software* tab in the *Software & Updates* application and install flash with..

---

### Post by howefield on 2016-12-18
> **daniell59 said:**
> Can you please expand upon the following. Enable Canonical partner repository  also  enable the Partners repository via the *Other Software* tab in the *Software & Updates* application and install flash with..

Search the Dash for the Software and Updates application and launch it.

Click on the Other Software tab as per the attached image and place a check against the Partner repository, close out and you will be prompted to reload your software sources, accept and the application should close automatically.

---

### Post by daniell59 on 2016-12-18
> **howefield said:**
> Search the Dash for the Software and Updates application and launch it.

Click on the Other Software tab as per the attached image and place a check against the Partner repository, close out and you will be prompted to reload your software sources, accept and the application should close automatically.

Thanks
Your images have made it more understandable for me. Later in the day, when my head clears from life's myriad of problems, I will follow up.

---

### Post by daniell59 on 2016-12-23
It has been several days and the error message has not appeared. I must say however, that I do not fully understand what I did. 

Thanks for the assistance.

---

### Post by howefield on 2016-12-23
> **daniell59 said:**
> It has been several days and the error message has not appeared.

Glad to hear it.

> I must say however, that I do not fully understand what I did.

Pepperflash is deprecated hence the error messages you experienced after attempting to install it, purging (completely removing) cleansed it from your system, including the error messages. Installing the recommended adobe-flashplugin worked as it should. No more complicated than that.

---

### Post by daniell59 on 2016-12-23
Now I use Chrome when I need flash.
I don't need to do more, since I intend to build a new computer soon, and with a new OS installation.

Thanks again!

---

