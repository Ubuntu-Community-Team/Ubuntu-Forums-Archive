---
title: "A few questions about GPG and PGP"
date: 2014-07-05
forum: General Help
---

### Post by J Tinsby on 2014-07-05
I have used PGP in Windows to encrypt my email for many years. Now using Ubuntu with Synaptic installed, I only see one package that seems to pertain to GPG it's only a signature verifier. I also see Enigmail for Thundebird to decrypt and encrypt mail.

The questions are:
Can I d/l only the Enigmail for Thunderbird or do I have to get a complete GPG program for the front end to run in Thunderbird?
Can I somehow import my keys from PGP into GPG?
 Are the two programs the same in the sense they are compatible with each other? 
Am I then able to send encrypted mail to someone using PGP in Windows?


Thank you

J T

---

### Post by Lars Noodén on 2014-07-05
[Enigmail](https://www.enigmail.net/documentation/) is a front end for gpg which is from the package GnuPG, which is included in your system.  

GnuPG is listed as a [dependency for Engimail](http://packages.ubuntu.com/trusty/enigmail) so if you install Enigmail, it will first check to ensure that you already have GnuPG.  As mentioned, it should be there already.

PGP, GnuPG and several other programs use the standard [OpenPGP](http://tools.ietf.org/html/rfc4880).  So, yes, you can use the same keys.  The standard and the programs have similar sounding names so it is a little confusing.

The two programs should be compatible in so far as they use the same standard.  

You can send encrypted mail to Windows users, but if they are able to decrypt it, that depends on how well their program supports the OpenPGP standard.  If they are using [GnuPG](http://gpg4win.org/) or something as good then things are ok.  Again, all that matters there is support of the OpenPGP standard.

---

### Post by J Tinsby on 2014-07-05
> **Lars Noodén said:**
> [Enigmail]("https://www.enigmail.net/documentation/") is a front end for gpg which is from the package GnuPG, which is included in your system.  

GnuPG is listed as a [dependency for Engimail]("http://packages.ubuntu.com/trusty/enigmail") so if you install Enigmail, it will first check to ensure that you already have GnuPG.  As mentioned, it should be there already.

PGP, GnuPG and several other programs use the standard [OpenPGP]("http://tools.ietf.org/html/rfc4880").  So, yes, you can use the same keys.  The standard and the programs have similar sounding names so it is a little confusing.

The two programs should be compatible in so far as they use the same standard.  

You can send encrypted mail to Windows users, but if they are able to decrypt it, that depends on how well their program supports the OpenPGP standard.  If they are using [GnuPG]("http://gpg4win.org/") or something as good then things are ok.  Again, all that matters there is support of the OpenPGP standard.

Hi Lars,

Thank you very much for the information, as I am new to Ubuntu I had no idea that GnuPG was included. or should be with the OS.

My friend in the UK is using a very old version of PGP 6.0.58 I believe. I hope that will be compatible with GnuPGP as you said. What amazes me is that more people don't use encryption for their email, once set up it's dead easy to use. If it's good enough for the NSA to use, it'll be fine for me. At least no network admin is going to be peeking at our conversations! :D

Thanks very much and I will let you know how I get on with it.

Cheers,

J T

---

### Post by J Tinsby on 2014-07-07
Not going all that well w/GnuPG. I see that I have v1.4.16 of GnuGP installed as Lars said it would be. I get the Enigmail options in the Thunderbird menu bar with icons to encrypt/ decrypt etc. Seem to be having trouble uploading a PGP public key to a keyserver. It looks to me that the ones that are shown in the menu, that you get in Enigmail / Thunderbird are not active currently. There is only one person I exchange mail with using encryption so I just have his public key and he has mine, neither are located on a keyserver. Suffice it to say I realize that at least for me to use his public key in enigmail, it has to be on a server somewhere, because that's where the program is looking. It's not looking locally for his key. Must I have seamonkey as well as Enigmail or just sort out the server stuff and it will be all right then? He will continue to use his version of PGP not Enigmail, so we need to find out if the two are compatible.

Thanks in advance!

J T

---

### Post by Lars Noodén on 2014-07-08
The keyserver is more a directory of keys so that you can find the public key of someone you *don't* already have the key for.  

If you have the public key for your friend, all you need is to import it into the GnuPG keyring.  If he has exported his public key and sent it to you, then you can import it using Engimail.  

Key management -> File -> Import Keys from File
Key management -> File -> Reload Key Cache

Or if you receive a signed message from him, you can click on the OpenPGP information menu in the displayed message and choose "import public key"

---

### Post by J Tinsby on 2014-07-08
> **Lars Noodén said:**
> The keyserver is more a directory of keys so that you can find the public key of someone you *don't* already have the key for.  

If you have the public key for your friend, all you need is to import it into the GnuPG keyring.  If he has exported his public key and sent it to you, then you can import it using Engimail.  

Key management -> File -> Import Keys from File
Key management -> File -> Reload Key Cache

Or if you receive a signed message from him, you can click on the OpenPGP information menu in the displayed message and choose "import public key"

Hi Lars,

Sorry I am not seeing either of those options under Key Management. When chosen I only get one box that opens and there's no way to have it search even the desktop for his public key. Don't ask me why that is. No option appears to Import or Reload Cache, I do see that one in another window but no way to have it do anything. I have the latest email from him sent from PGP 6.5.8, its not PGP signed, but again no clicking of any of the options in Thunderbird will load anything. I have his public key right on my Unity desktop.

Sorrry to be so much trouble, this should be relatively easy.

Thanks,

J T

---

### Post by Dennis N on 2014-07-08
Since Lars is offline, if you are trying to import a public key, I'll suggest that in the terminal, you can import someone's gpg public key file with:
```
gpg --import keyfile
```
For keyfile, substitute the path and file name of the public key file to be imported.

It should then be usable by Enigmail, although I have never used Enigmail myself.

---

### Post by J Tinsby on 2014-07-08
> **Dennis N said:**
> Since Lars is offline, if you are trying to import a public key, I'll suggest that in the terminal, you can import someone's gpg public key file with:
```
gpg --import keyfile
```
For keyfile, substitute the path and file name of the public key file to be imported.

It should then be usable by Enigmail, although I have never used Enigmail myself.

Hi Dennis,

Thank you very much for jumping in. What you need to know is right now I am trying to do is import the key to a keyserver using Windows since I don't know how to xfer the public key to my Ubuntu.

Any thoughts on that problem? If I get the time to spend I hope I can upload his one key to a server so that Enigmail will find it or GnuPG will

Thanks@

J T

---

### Post by Dennis N on 2014-07-08
> **J Tinsby said:**
> Hi Dennis,

Thank you very much for jumping in. What you need to know is right now I am trying to do is import the key to a keyserver using Windows since I don't know how to xfer the public key to my Ubuntu.

Any thoughts on that problem? If I get the time to spend I hope I can upload his one key to a server so that Enigmail will find it or GnuPG will

Thanks@

J T

You wrote "import the key to a keyserver" but I assume you meant **export**? Then once there, anyone (literally) can get it from the keyserver - the idea is to get your key out in public. (If it is not your own public key, what would the other person think about this?)

You can go to [http://pgp.mit.edu/](http://pgp.mit.edu/) and paste in a public key in text format in the box to place it on their keyserver.

Create the key in text format (saved to a file public_key.asc) with:

```
gpg --armor --output public_key.asc --export KEYNAME

```
KEYNAME is the email address identifying this public key.

(I assume Windows has a PGP application and you can use a command line with this or a similar command - otherwise a gui application should have an option to export a key in ascii text format to a file.)

Copy and paste the entire content of public_key.asc into the submission box at the website.
Sample Content:

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.11 (GNU/Linux)

mQENBEpWTPIBCAC3bXByRxU2IH/26EzwphR/54R3s6ge7hMFI3ETMWdTM/Kl+zbM
lla5CsIaLXT92Jb7Ypl0cXwh1sW24QBgxllNDFANo/0hI05ft2p37tdbI61ufgqP
Td1DzqxgXHpht/L6M2Fa6W80OfhmzsxF7oMe0hyXhNzbXmgS/rZquKawfv8Ew2CR
EyXHNV+VDRZLYhjwlari+OUq/GvO//AhDGT2EOsYxgPEy+W6mBNKLw8jzkPvM+4q
P2yzB34FCrtZx3OxFJFvC+VuH25MqMceDyjecEUayDsGwXtsNCr+gfO6u293/Olu
reubW96vBGCpyfRX9DjopKaFTRP8pnFK4agfABEBAAG0KkV4YW1wbGUgS2V5IEhv
bGRlciA8ZXhhbXBsZUBzb21ld2hlcmUubmV0PokBPAQTAQIAJgUCSlZM8gIbAwUJ
EswDAAYLCQgHAwIEFQIIAwQWAgMBAh4BAheAAAoJEJT2Dn71Ur7/yZsH/RPzmP2v
xCTwFLcuwq2aiNgVguJ2E+GP1EP19CKD3dd51IDtDKHxisoXGM+73t5oDZZEqwcX
Xu8wqTB0JHjX38nq/F7suRJWOYU6SBLdWhCq+n0/zegVusI/bEQHk/WLcdvh6zVp
ZNFuWRI+HWgvjJHMfqai9piMpINjf/z6bCyAP4aVanLWy6QEZAzmJAJyjUPOMzC2
H/WUbdST05O9i/mtVH+WRmnSj3ahVx9K5D9bN6PAyS6EwRdvnvSVv7QAwhILmg+u
kPu6yfxjxXG1tj/Qvs65ECQxMUlOBvq96Y7KETDCpIk69u9FMIEt5BMOq6xlPH0s
8QoE2M5r8CxI+yW5AQ0ESlZNUwEIANvGlJRhlXh2Ql3unotFQ9FMBl+8T8/YNHmP
lsQQsSc0m5ybiC1rLjOsIWptsSdD4GG/spaZWVc9e/V/3NyYcG6Ou4DaYFiG6qHa
7+hqLL8RKaZSBw35YUSef9HCwKwH3CNc3gk+aikBUO57o8s/H0WObb+mnkDuoFoK
U+j+fxqYVJyThTuSy9WhVgpRGY9qKKm59Gy3/Sa9laCecY9N91q9veyiu2npgSQQ
NxAlYVYrPbR6tEBClQNUPWx3WH2WcQL556FwwvR9cFsKaQWTm/K0O+586b0I3VI/
oCoCF5V9lNeUVeLEtZwdfIrC4q+1D9PMG1UrQwWsQ0jDYDjyJh0AEQEAAYkBJQQY
AQIADwUCSlZNUwIbDAUJEswDAAAKCRCU9g5+9VK+/8GlB/9If2w0TjAW7wPIfvov
4YwRd/eyaDWS0xI5Az4YNaTIIfDYltHLbPue+eS1nekTl0HN2QdChcqkuHlU5bho
wAs2ljob5McWFFveaEX93mKqtRilbdpStuHlz02pjJtHhyAxcOGEMx3e+3E2oRIO
SEJXzeqA1jwOPPx1QPxdcz2y7xJITH0WhC2YPeDfJnHP2qirCfszltA6ztq7Xehf
YdKzxKQRq4guQAuav49EqittjwxMOl3M5CaOlTlTOsr21GpU3ipJX1OetaeBaz8H
fN8MvRlW2m9ZBdOwgF4QFmbnah7xTOcpe6d2rJTdWbZkYX9agCE1THerEmkurkYV
Yoqe
=wG1E
-----END PGP PUBLIC KEY BLOCK-----
```

That said, I would personally choose to take the file public_key.asc and just import it into Ubuntu with the command in post #7. You can also just email the file as an attachment to anyone you want to have it, unless your goal to to make it available to everyone in the world in which case use the keyserver.

Remember, if it is your own public key you are importing into Ubuntu, you also need to import your secret (private) key, and you never make that public - you would have to transfer that by the post #7 command line method, or using Enigmail's import key options (I am not familiar with Enigmail).

Your choice how to proceed!

---

### Post by J Tinsby on 2014-07-09
HI Dennis,

You are correct in that I don't need to export the friend's key to a keyserver, we never had to do that before. I just need to get the silly key imported into GPG on my local machine. What I am having trouble with now is finding the correct path statement to use to load the key. The public key resides on the Unity desktop but it has an odd name that I think is messing up loading the file. The pub key is called " joe's public key.asc" ( no quotes ) I am trying to use the terminal by typing what you have in #7

IE: gpg --import/home/desktop/joe's public key.asc of course that fails either due to the path statement or the name of the .asc file. What is the correct path statement for a file on the desktop? And can I rename his .asc key to a name with only one word in it with no spaces? Or he needs to send me a new key with one name in it?

Many thanks for your help!

J T

---

### Post by Lars Noodén on 2014-07-09
> **J Tinsby said:**
> Sorry I am not seeing either of those options under Key Management. 

When the key management window is open and active, try moving the mouse up to the top of the screen.  Then the other menus will become visible.  This is a quirk / drawback to the Unity interface.  

In the shell method, about the path names, you can wrap them in quotes or escape the tricky characters with backslashes.

```

gpg --import "/home/desktop/joe's public key.asc"
gpg --import /home/desktop/joe\'s\ public\ key.asc

```

---

### Post by Lars Noodén on 2014-07-09
If you try typing using tab-completion, the backslashes get filled in for you, usually.

---

### Post by Dennis N on 2014-07-09
> **J Tinsby said:**
> I am trying to use the terminal by typing what you have in #7

IE: gpg --import/home/desktop/joe's public key.asc of course that fails either due to the path statement or the name of the .asc file. What is the correct path statement for a file on the desktop? And can I rename his .asc key to a name with only one word in it with no spaces? Or he needs to send me a new key with one name in it?

Many thanks for your help!

J T

The spaces in the file name cause a problem and the path you show is not right either. [FONT=Courier New]**/home/desktop**[/FONT] is not your Desktop folder, it should be [FONT=Courier New]**/home/your-username/Desktop**[/FONT] or simply [FONT=Courier New]**~/Desktop**[/FONT] (Desktop is usually capitalized in Ubuntu - check if yours is.)

Yes, you can rename the key to something simple without spaces or other punctuation like **joe-smith-key.asc** That has no effect on what gets imported.

In my terminal, the command to import that keyfile would be:

```
dmn@Zotac:~$ gpg --import ~/Desktop/joe-smith-key.asc
```

The terminal will give you a confirmation that it was done.

---

### Post by J Tinsby on 2014-07-09
> **Lars Noodén said:**
> When the key management window is open and active, try moving the mouse up to the top of the screen.  Then the other menus will become visible.  This is a quirk / drawback to the Unity interface.  

In the shell method, about the path names, you can wrap them in quotes or escape the tricky characters with backslashes.

```

gpg --import "/home/desktop/joe's public key.asc"
gpg --import /home/desktop/joe\'s\ public\ key.asc

```


Lars,

Thank you very much as well as Dennis,        for helping me with this. I would have never thought to move the cursor up to the screen edge to see the other menus, that was the method I used, and it WORKED! :D I was able to decrypt my friends message once I had my key and his public one imported to GPG. This will be great not having to change to the dreaded XP to use my PGP program!

I haven't had Ubuntu installed for very long, *as if you guys can't tell already*, but I am enjoying the challenge of making things work and learning the various terminal commands. I doubt that I will ever learn them all is all I can say, it does remind me in some ways of DOS and the command prompt and syntax needed to make the system work.

So yet another hurdle has been elminated in Ubuntu and I am glad of it.

Best wishes and regards and many thanks for all the help, it's working now! I have yet to send him a test message but I will send one to myself first and go from there, I don't foresee any troubles.

I must say that all the help I have gotten from this forum has prevented me from giving up and running away screaming so it's most appreciated is all I can say! It's done just the opposite, I look forward to using ubuntu and seeing how much I don't know.

J T

---

### Post by J Tinsby on 2014-07-11
One more question that I should know the answer too but don't.

What is the proper use of the S/Mime option? My friend and I only send text messages and are content that it works. I have always had trouble sending photo attachments in a PGP message, unless I send it as a separate message. Would S/Mime allow me to do this?

I know the thread is marked as solved but I hope maybe Lars or someone will find this last question I have.

Thanks!

J T

---

### Post by Lars Noodén on 2014-07-12
I don't do so much with attachments, institutional filesharing / NAS is the way to go, so I can't add much.  Others will know much more.  

PGP/MIME can be set in Edit->Account Settings->OpenPGP Security.

---

### Post by J Tinsby on 2014-07-12
Lars,

That's fine I understand. Thanks again!

J T

---

