---
title: "Acrobat PDF reader for Gutsy"
date: 2007-10-11
forum: General Help
---

### Post by stchman on 2007-10-11
Since Adobe Acrobat reader is not in the repos, can you use the .deb acroread from Feisty?  I prefer Acrobat over Evince for reading PDFs.

Thanks

---

### Post by swisscow on 2007-10-12
Actually if you add the medibuntu repositories then aroread (acrobat reader) is there.

---

### Post by stchman on 2007-10-12
> **swisscow said:**
> Actually if you add the medibuntu repositories then aroread (acrobat reader) is there.

I went to medibuntu website and they don't tell you how to add the repos to Gutsy.  Do you use the Feisty repos for Gutsy?

---

### Post by swisscow on 2007-10-14
I have the Gutsy repositories - below are the relevant lines form my sources.list



```
# Medibuntu.  
deb http://packages.medibuntu.org/ gutsy free non-free
```

---

### Post by mahiyar on 2007-10-16
This gives the gpg key missing error

---

### Post by por100pre1 on 2007-10-16
> **mahiyar said:**
> This gives the gpg key missing error

Be sure to add the key:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by mahiyar on 2007-10-17
That will be great I guess I will then be able to install libdvdcss also which will solve my DVD player problem also.

---

### Post by chunchengch on 2007-10-17
You could visit the Adobe website to download the latest version deb file **AdobeReader_enu-8.1.1-1.i386.deb**.

---

### Post by por100pre1 on 2007-10-17
> **stchman said:**
> I went to medibuntu website and they don't tell you how to add the repos to Gutsy.  Do you use the Feisty repos for Gutsy?

The instructions are there, be sure to check [www.medibuntu.org](www.medibuntu.org) .

Here's a direct link to the how-to:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by stchman on 2007-10-17
> **por100pre1 said:**
> The instructions are there, be sure to check [www.medibuntu.org](www.medibuntu.org) .

Here's a direct link to the how-to:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

You can understand my confusion.  If I go to medibuntu website and look at this page:

[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

They do not speak of Gutsy.

If I then go to this page:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

It talks of adding the repository to Gutsy.

I wonder why medibuntu has not updated their site?

---

### Post by fudo81 on 2007-10-27
I followed the instructions and installed acroread successfully. I can't find its plugin for Firefox, though. In older Ubuntu releases, it used to be in a package called mozilla-acroread. Should I add other repositories (apart from Medibuntu) to get it?

---

### Post by por100pre1 on 2007-10-27
> **fudo81 said:**
> I followed the instructions and installed acroread successfully. I can't find its plugin for Firefox, though. In older Ubuntu releases, it used to be in a package called mozilla-acroread. Should I add other repositories (apart from Medibuntu) to get it?

Yes add mozilla-acroread. That's the plugin.

```
sudo apt-get install mozilla-acroread
```

> **stchman said:**
> You can understand my confusion.  If I go to medibuntu website and look at this page:

[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

They do not speak of Gutsy.

If I then go to this page:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

It talks of adding the repository to Gutsy.

I wonder why medibuntu has not updated their site?

I agree. They should update the old page, redirect to the new page, or replace the old page with a link to the new one.

---

### Post by fudo81 on 2007-10-27
> Yes add mozilla-acroread. That's the plugin.
```

sudo apt-get install mozilla-acroread

```

When I try to do so, I get the following answer:
> 
Il pacchetto mozilla-acroread non ha versioni disponibili, ma è nominato da un altro
pacchetto. Questo significa che il pacchetto manca, è diventato obsoleto
o è disponibile solo all'interno di un'altra sorgente
E: Il pacchetto mozilla-acroread non ha candidati da installare

which roughly translates to:
The mozilla-acroread package has no available versions, but it is mentioned by another package.
This means that the package is missing, has become obsolete, or is only available from a different source.
E: The mozilla-acroread package has no candidates to install.

So... what?
Thanks for your help.

---

### Post by por100pre1 on 2007-10-27
Open Synaptic, and try to add it from there.

---

### Post by peebly on 2007-10-27
Hello

If you downloaded acrobat reader from adobe. When you install it, it will install the Mozilla plug-in for you.

To get it, go to adobe, click get acrobat, For some reason mine comes up with Linux.(rpm) if it does just click choose a different version.

Then select Linux, then select Linux installer, choose Linux -x86 (.deb), then your language.

Now click continue then click download adobe reader.

When downloaded just double click on the downloaded file, then click install package it will also install the Mozilla plug-in.

---

### Post by fudo81 on 2007-10-28
Well, I'm afraid of being repetitive, but the package does NOT appear in Synaptic!
It's not in my repositories, which include Medibuntu... it simply doesn't exist, as far as my system knows.

I just found out what the problem is, and I guess it's not very easy to solve - at least without resigning and installing Adobe Reader from the Adobe site.
The fact is that for some strange reason, in the Medibuntu repository the mozilla-acroread package only exists for i386 architectures, but I'm running an amd64 Ubuntu... d'oh!
Thanks again.

---

### Post by lorebett on 2007-10-29
> **fudo81 said:**
> I followed the instructions and installed acroread successfully. I can't find its plugin for Firefox, though. In older Ubuntu releases, it used to be in a package called mozilla-acroread. Should I add other repositories (apart from Medibuntu) to get it?

Hi

I've only started to use (K)ubuntu for a few days (I'm coming from Debian), and I was wondering whether it is enough safe to use also Medibuntu repositories... I mean, I found lame also on the ubuntu repositories and there's one also in Medibuntu... so which one then should I use?

thanks in advance

---

### Post by saltydog on 2007-10-30
Add medibutuntu repositories..

---

### Post by Cochise on 2007-10-30
after adding the repo make sure you type sudo apt-get update from a terminal

---

