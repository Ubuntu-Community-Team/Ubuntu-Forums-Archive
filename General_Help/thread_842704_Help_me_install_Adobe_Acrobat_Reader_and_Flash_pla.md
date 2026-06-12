---
title: "Help me install Adobe Acrobat Reader and Flash player"
date: 2008-06-27
forum: General Help
---

### Post by Zdravko on 2008-06-27
I tried to download and install Adobe Acrobat reader from the official web site. But ff3 refused to open the rpm file, because this format was not associated with an application.
I also tried to install the adobe flash player again from the same site. This time I chose the tar.gz format. It opens the archive but then I have no idea what to do with the containing files.
Now it is your turn to help me!

---

### Post by perlluver on 2008-06-27
> **Zdravko said:**
> I tried to download and install Adobe Acrobat reader from the official web site. But ff3 refused to open the rpm file, because this format was not associated with an application.
I also tried to install the adobe flash player again from the same site. This time I chose the tar.gz format. It opens the archive but then I have no idea what to do with the containing files.
Now it is your turn to help me!

To install flash paste this in a terminal ```
sudo apt-get install flashplugin-nonfree
``` or ```
sudo apt-get install ubuntu-restricted-extras
``` for adobe reader, look up [Medibuntu]("http://www.medibuntu.org/").

---

### Post by drs305 on 2008-06-27
> **Zdravko said:**
> I tried to download and install Adobe Acrobat reader from the official web site. But ff3 refused to open the rpm file, because this format was not associated with an application.

Adobe Acrobat is in the medibuntu repositories. It's called acroread.
```
sudo aptitude install acroread
```

If you don't have the medibuntu repository enabled, add it with:
```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

---

### Post by Zdravko on 2008-06-29
Okay, I will give it a try...

---

### Post by Zdravko on 2008-07-05
Thanks! It works!

---

### Post by Zdravko on 2009-02-08
If I don't want to add this repo, what can I do to install acrobat reader?

---

### Post by drs305 on 2009-02-08
> **Zdravko said:**
> If I don't want to add this repo, what can I do to install acrobat reader?

You can go to this site and download it in various formats (.tar.gz, .rpm, .deb) and install it yourself. 
[http://get.adobe.com/reader/otherversions/]("http://get.adobe.com/reader/otherversions/")

Of course, not having a repository means no updates. You could always install it via the repository and then disable the repository by *unticking* it in synaptic. It would then be available  for activation  whenever you want to update the installation.

---

### Post by Zdravko on 2009-02-08
Thanks. I decided to add medibuntu repo. Now I am installing acroread... Then you have to tell me how to kick that repo out!

---

### Post by drs305 on 2009-02-08
> **Zdravko said:**
> Then you have to tell me how to kick that repo out!

Once you have installed the app, open Synaptic (if not already open) and go to Settings > Repositories > Third-Party. You will see a checkbox with a listing for "*[http://packages.medibuntu.org/](http://packages.medibuntu.org/)*". Deselect the checkbox and you have disabled the medibuntu repository. If you want to enable it later, just tick the checkbox.

---

### Post by Zdravko on 2009-02-08
Yay, I did click on remove. Now it is gone... forever?
Why is Adobe reader in English? I wish it was in German... :(

---

### Post by drs305 on 2009-02-08
> **Zdravko said:**
> Yay, I did click on remove. Now it is gone... forever?
Why is Adobe reader in English? I wish it was in German... :(

"Forever" if you want, but available if you re-enable it by ticking the checkbox.

There should be a way to get the German version from the repositories - someone can probably tell you or you can do a search of the forums. 

On the link I gave you, below the OS selection was a language selection. German is available if you would prefer to install it manually. Download the .deb file and double-click - it should install.  *Ausgezeichnet!*

---

### Post by albinootje on 2009-02-08
> **Zdravko said:**
> I decided to add medibuntu repo. Now I am installing acroread... Then you have to tell me how to kick that repo out!

Adding a repository, then install an application via that freshly added repository, and then remove that same repository will mean that you will not get information about (security) updates for that application in the future!
Why do you want to remove that repository again ?

---

### Post by Zdravko on 2009-02-08
> **drs305 said:**
> "Forever" if you want, but available if you re-enable it by ticking the checkbox.

There should be a way to get the German version from the repositories - someone can probably tell you or you can do a search of the forums. 

On the link I gave you, below the OS selection was a language selection. German is available if you would prefer to install it manually. Download the .deb file and double-click - it should install.  *Ausgezeichnet!*
Yuppie! That is what I am doing. I removed the acroread. Then I went to the adobe reader site and choose another version - a deb in Deutsch!
albinootje, I may reinstall Adobe reader in a few months. This is the purest way of updating :)

---

### Post by scouser73 on 2009-02-08
> **Zdravko said:**
> I tried to download and install Adobe Acrobat reader from the official web site. But ff3 refused to open the rpm file, because this format was not associated with an application.
I also tried to install the adobe flash player again from the same site. This time I chose the tar.gz format. It opens the archive but then I have no idea what to do with the containing files.
Now it is your turn to help me!

You should download the (.deb) file from Adobe.

---

### Post by Zdravko on 2009-02-08
> **scouser73 said:**
> You should download the (.deb) file from Adobe.
Thats what I did :)

---

