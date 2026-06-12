---
title: "Firefox 3.0 upgrade issue"
date: 2008-06-03
forum: General Help
---

### Post by Chandler Mike on 2008-06-03
Well, I jumped the gun a week or so ago and upgraded Firefox manually, because I just couldn't wait for Ubuntu to add it to the update tool.

Now it wants to upgrade it and it wont...I keep getting the Partial Upgrade box, and then a:

It was not possible to authenticate some packages.

firefox
firefox 3.0
firefox 3.0 gnome support
firefox gnome support

What can I do guys to get this back to normal? Sorry for being such a noob, but I really am :)

---

### Post by iaculallad on 2008-06-03
> **Chandler Mike said:**
> What can I do guys to get this back to normal? Sorry for being such a noob, but I really am :)

If what you mean by "get this back to normal" is downgrading your Firefox version, try doing this in your terminal:

```

sudo apt-get purge firefox-3.0
rm -r ~/.mozilla/firefox
sudo apt-get install firefox-2
```

---

### Post by Bubba64 on 2008-06-03
> **Chandler Mike said:**
> Well, I jumped the gun a week or so ago and upgraded Firefox manually, because I just couldn't wait for Ubuntu to add it to the update tool.

Now it wants to upgrade it and it wont...I keep getting the Partial Upgrade box, and then a:

It was not possible to authenticate some packages.

firefox
firefox 3.0
firefox 3.0 gnome support
firefox gnome support

What can I do guys to get this back to normal? Sorry for being such a noob, but I really am :)

How did you install in the first place if you used the launchpad install the upgrade has a xulrunner rc2 that goes with the rc2 upgrade.
I have never had a problem with any version of FF3 I had it installed in Gutsy to. It is not authenticated because you are probably using the launchpad download 3rd parties always have this misnomer.

---

### Post by Chandler Mike on 2008-06-03
> **iaculallad said:**
> If what you mean by "get this back to normal" is downgrading your Firefox version, try doing this in your terminal:

```

sudo apt-get purge firefox-3.0
rm -r ~/.mozilla/firefox
sudo apt-get install firefox-2
```


Well, I guess by "back to normal" I want to be able to use the Ubuntu updater instead of manual installs.

Do I need to go back to Firefox 2 to make this happen?

Do your instructions above purge my profile?

---

### Post by Chandler Mike on 2008-06-03
> **Bubba64 said:**
> How did you install in the first place if you used the launchpad install the upgrade has a xulrunner rc2 that goes with the rc2 upgrade.
I have never had a problem with any version of FF3 I had it installed in Gutsy to. It is not authenticated because you are probably using the launchpad download 3rd parties always have this misnomer.

I just downloaded the tar.gz file from the firefox site and manually installed it. Was a big pain to try and get my old profile back as the default too.

---

### Post by Bubba64 on 2008-06-03
> **Chandler Mike said:**
> I just downloaded the tar.gz file from the firefox site and manually installed it. Was a big pain to try and get my old profile back as the default too.

I hope the instructions from the other posters have fixed your problems.

It seemed besides wanting to get a working version of Firefox going that you were concerned about the not authenticated Thang, any download not from the main distribution  is always marked this way, in other  it looks like the proposed portion of software sources was the source of the unauthenticated download. You can get the Latest FF3 rc2 from Launchpad that is a direct overwrite of FF3 from Hardy, my downloads have had no problems. I have the proposed repositories in software sources always on and when the FF3 rc1 was in their download I had it already from Launchpad so proposed didn't mess with any downloads. I don't know if this launchpad version will limit any final FF versions, but at this point they are releasing rc2 when proposed in hardy updates is only releasing rc1. I think either one will end up with the final and the only thing I would wonder about is the upgrade to the next distribution, which I don't think will be effected. In case you want the Launchpad download info here it is, also launchpad is a well respected purveyor of distributions.
[http://www.ubuntugeek.com/how-to-install-firefox-3-rc1-in-ubuntu-hardy.html](http://www.ubuntugeek.com/how-to-install-firefox-3-rc1-in-ubuntu-hardy.html)
This link says how to install rc1 but it is just instructions on how to include the repository in your 3rd party list it is downloading rc2 at this time. Good Luck

---

### Post by navneeth on 2008-06-03
> **Chandler Mike said:**
> I just downloaded the tar.gz file from the firefox site and manually installed it. Was a big pain to try and get my old profile back as the default too.

[off-topic]

If you want to save your current profile in a nice, cozy corner in the hard disk, and the reinstall it later in a couple of seconds, use [FEBE](http://customsoftwareconsult.com/extensions/febe/febe60.html). For now, for Firefox 3 and above, the only option is the beta of version 6. And for Firefox Beta 5, the current beta of FEBE does not work, so I use 6.0b(20080512_152139), and it does what it is supposed to. 

I recently went through the pain of reinstating my usual profile on a new profile of Fx. I did have it backed-up, but I think there was something "inherently" wrong with it. 

[/off-topic]

---

