---
title: "how to encrypt message (not file) in terminal?"
date: 2013-03-02
forum: General Help
---

### Post by asteriks on 2013-03-02
Hi, I am interested how to encrypt message in terminal (with friend gpg public key which I import)? I use Ubutnu precise.
I don't need encryption of file then message, 
_this is not what I need:_ gpg -o encrypted_file.gpg --encrypt -r <KEY-ID> original.file
because it will give me encrypted file and not message in terminal.

for example I can write some message in Terminal and then I need to encrypt it, and copy into email.
I know to use: **cat > file.txt**
*then I write some message*, press ctrl+c to finish message in cat command, but I need to encrypt mesage and copy into email.
result can be in terminal or in file.txt, but words should be encrypted. then I can copy it.

---

### Post by rnerwein on 2013-03-02
hi
i  propose dont' use Ctrl C ( this means cancel ) use: Ctrl D -> this is EOF.
cheers

---

### Post by sudodus on 2013-03-02
Maybe ***Enigmail*** in Thunderbird would make it convenient for you. Then you can type your message directly into the Thunderbird Write (new mail) window and get it encrypted. See this link

[http://www.enigmail.net/home/index.php](http://www.enigmail.net/home/index.php)

---

### Post by sudodus on 2013-03-02
This way you can operate with terminal commands to encrypt in ascii style for your friend [COLOR=#0000ff]joe[/COLOR] (finish the input with ***ctrl + d***)
```
[COLOR=#0000ff]gpg -aer joe[/COLOR]
[COLOR=#008000]now I'm writing this (line 1)
and that (line 2)
and finish with ctrl + d (line 3)[/COLOR]
-----BEGIN PGP MESSAGE-----
Version: GnuPG v1.4.11 (GNU/Linux)

hQIOA9XUygxXFBIkEAgAiAJltX6kdLcbjpoWd/OJjwseaO9KJ6LPMI2jiV7l7n4F
5uITDW8rP/7NPl/ZwbgvP4uVGTirIA48/XOXg8ru66qOVbpXvVPMbLlAPZhPy69/
b4Bw+mWXbCZpbwJNX8oK66skOiYRkdmeLH/YGA2E0m47lTnlZ23wGnCsdVems1NA
OPHC78P6y8TAqcD4XqFbwSFxm7mWNTsEIMTx5LGa/PzBev3ZNdRXlPB/hYk8NsYo
fRH1RIFPjYSeEranL+wfl2ytHioDwAgHqot008DyorRBpcGIScvhkTLl2GpnPvJE
mI0CqWUon5ZzwN/2yLr5RqAlaMKN2abZKXF5mdkjYgf/TFOyoIWiBhcjDYCGs/If
+oYvtP9qMf6iEUFQZ4jtGZm3RF91GBex/X6Wn3YExVZnEtw/k6pWjjFTqORcftG/
5Jd3zv78eL4ZiQErwrUzfRh6Igu0ckqL/Ghj5F/SPdt6ff6U6fXRySHxVAgtm8cR
gly91CYYz5qXvJqEi4b68oio147W4jijOgz3f3Jpg6D3XpaKtclzT6QNST22ePlo
2Wki0X8kHqXkHcJ2XR8YF1PzLhi6hSKDNhEdhrMI8/3a+lM7KtVcixbem40Idz5X
3gBWaolaB91sxF2BPz5et3Q2ssHGLBEZmIJgpnpgqAmReip/fbaPps4Lbrsniuwg
EtJ+AUHrot0Jjh0UxNs3tGKRY6y8EihERm3oi+9KACpLYL8KBczhYiMdM5CUMpaI
pqWoDIZmCByjp9Yctzp2ph6DB0fwwyJwMM7fbdDRAjemcQ11TUNKOBCRWZZPs3RP
T0Xs44ERzReRoapa4dJj9ET/vsRstsYQfGsBMl869EU2
=h9Oj
-----END PGP MESSAGE-----

```
And this ascii block of data will contain the message you typed.
```

[COLOR=#008000]now I'm writing this (line 1)
and that (line 2)
and finish with ctrl + d (line 3)[/COLOR]

```
I checked, that it works for me :-)

---

### Post by asteriks on 2013-03-03
**Hi, thank you very much, it worked for me too. **
I imported public key, then wrote [COLOR=#ff0000]gpg -aer olala[/COLOR] and wrote the message in terminal and used ctrl+D and I got it encrypted.

jut to ask, **what would be the way to decrypt it in terminal?**

I tried gpg -adr olala
then  I copy pasted encrypted message but I didn't get place to write  password, it just told me I need password to decrypt message. here it is:

```
ubuntu@ubuntu:~$ gpg -adr olala
-----BEGIN PGP MESSAGE-----
Version: GnuPG v1.4.11 (GNU/Linux)

hQIMA3gwz0AvAPRxARAAr/vvX6tmOJq/JUz4azv4z92WaTAPRIkMpzdtW7MUnbb9
TJGEoCDJYJH+26AfIO9uBDlRmD/BUey+59d1a7bOTdb9JK9/AIbF8m9Xp1vh2a6A
zHnpl+FD/BUupd6CdY6ymy9gK7LMYJE3H2STIXcOfScalZFvc8IkGuV+SxZiMl7y
QDytKJMAfl7z6j/7YfFJet8Ud+WvOFsXBx0QPvdB09AI+Hh3sh9JQzTI8tJCrEU1
wTq0z7paPyElsikiv6vNnH/t7b5TRGEBk7yIoES7qmYGGuKil8dHkFKupgXbd2v8
Hbevl1RmryVFQ3vbiY/TYP2Fl/8JwbHSnEWY+djn897vQNP0Dgg2NGgWcLd418PX
lE5Ug1S0p2JYhKRL7CPKTTr9VBzwdoWxst7NQZqOjdbY5/twWHBo3ZWr5FHV8aV9
wqu60aDti9BRjwjPNIxtA/zLTSP4MOXYNacvijDHfaDLS/3jDfQS6zlcNRPKalqC
F9alh3JaNsryvXwQXtduFXuZ2pLUNxca21BFU7g5UpzU/3qE4mCYj8FVEg/scGpZ
xdQoIwvezuSxfXNajoVhiv3WSgyOiZzFBHAlQLQvo/7FGFDEv8I9PrPXXDiPdXTe
jM7hKrItvVvExXuIR+Cd9X/6nkyij2Tyn9mV7KkHBuG00p8GmwF0mTJ5w7do73HS
YQF/DpJ9omkrR0YfZEeK8+ZuN8Hhfjw/F1OdHD35HKcbagaTsuHAHxTpzbzBUlaz
wsdd1lXBp3P5XgU5FdxJX/i/OHLVmlPWx5TCMue4ClfAH+2pL6NG8TBA7rQ8RvKK
POk=
=ucjZ
-----END PGP MESSAGE-----
You need a passphrase to unlock the secret key for
user: "olala <olala@ola.com>"
4096-bit RSA key, ID 2F00F471, created 2013-03-03 (main key ID 795E1C64)

gpg: encrypted with 4096-bit RSA key, ID 2F00F471, created 2013-03-03
      "olala <olala@ola.com>"


```

---

### Post by zero2xiii on 2013-03-03
Hay,

Just out of curiosity, how hardcore encrypted do you need? If a simple shifting cypher will do there is a lovely sed command that can help you.

PS, I THINK "joe" is the password for the encrypting section, so it should be the same for decryption. If not, you need the same key on both systems to encrypt and decrypt messages.

Good luck

EDIT:
SED Shifting Cypher:
```
echo "Hullo this is a test sentence" |sed y/abcdefghijklmnopqrstuvwxyz/qwertyuiopasdfghjklzxcvbnm/

Hxssg ziol ol q ztlz ltfztfet

```
Nice and easy. Not very secure, but You cant read the "encrypted" message just by sight. You will need to shift it back to the original alphabetical sequence.

---

### Post by sudodus on 2013-03-03
> **zero2xiii said:**
> 
PS, I THINK "joe" is the password for the encrypting section, so it should be the same for decryption. If not, you need the same key on both systems to encrypt and decrypt messages., but You cant read the "encrypted" message just by sight. You will need to shift it back to the original alphabetical sequence.

No joe is the name of the public pgp key. This is unsymmetrical encryption with a public key, and the message can only be decrypted with the receiver's private key. This is much safer than for example encrypted zip files. Read more at this link :-)

[[COLOR=#ff0000]https://en.wikipedia.org/wiki/Pretty_Good_Privacy[/COLOR]]("https://en.wikipedia.org/wiki/Pretty_Good_Privacy")

---

### Post by sudodus on 2013-03-03
> **asteriks said:**
> **Hi, thank you very much, it worked for me too. **
I imported public key, then wrote [COLOR=#ff0000]gpg -aer olala[/COLOR] and wrote the message in terminal and used ctrl+D and I got it encrypted.

jut to ask, **what would be the way to decrypt it in terminal?**

Do like this (step by step) to decrypt in terminal. You need the corresponding private key (in this example a key named '[COLOR=#ff0000]olala[/COLOR]'). In the real case only you have your private key and only your friend has her/his private key. So you cannot decrypt what you have encrypted for someone else.

```
gpg -d (enter)
(paste pgp message)
type passphrase (enter)
ctrl + d
```
And you'll get the message on the screen

```
$ [COLOR=#0000ff]gpg -d[/COLOR]
-----BEGIN PGP MESSAGE-----
Version: GnuPG v1.4.11 (GNU/Linux)

hQIOA9XUygxXFBIkEAgAiAJltX6kdLcbjpoWd/OJjwseaO9KJ6LPMI2jiV7l7n4F
5uITDW8rP/7NPl/ZwbgvP4uVGTirIA48/XOXg8ru66qOVbpXvVPMbLlAPZhPy69/
b4Bw+mWXbCZpbwJNX8oK66skOiYRkdmeLH/YGA2E0m47lTnlZ23wGnCsdVems1NA
OPHC78P6y8TAqcD4XqFbwSFxm7mWNTsEIMTx5LGa/PzBev3ZNdRXlPB/hYk8NsYo
fRH1RIFPjYSeEranL+wfl2ytHioDwAgHqot008DyorRBpcGIScvhkTLl2GpnPvJE
mI0CqWUon5ZzwN/2yLr5RqAlaMKN2abZKXF5mdkjYgf/TFOyoIWiBhcjDYCGs/If
+oYvtP9qMf6iEUFQZ4jtGZm3RF91GBex/X6Wn3YExVZnEtw/k6pWjjFTqORcftG/
5Jd3zv78eL4ZiQErwrUzfRh6Igu0ckqL/Ghj5F/SPdt6ff6U6fXRySHxVAgtm8cR
gly91CYYz5qXvJqEi4b68oio147W4jijOgz3f3Jpg6D3XpaKtclzT6QNST22ePlo
2Wki0X8kHqXkHcJ2XR8YF1PzLhi6hSKDNhEdhrMI8/3a+lM7KtVcixbem40Idz5X
3gBWaolaB91sxF2BPz5et3Q2ssHGLBEZmIJgpnpgqAmReip/fbaPps4Lbrsniuwg
EtJ+AUHrot0Jjh0UxNs3tGKRY6y8EihERm3oi+9KACpLYL8KBczhYiMdM5CUMpaI
pqWoDIZmCByjp9Yctzp2ph6DB0fwwyJwMM7fbdDRAjemcQ11TUNKOBCRWZZPs3RP
T0Xs44ERzReRoapa4dJj9ET/vsRstsYQfGsBMl869EU2
=h9Oj
-----END PGP MESSAGE-----
You need a passphrase to unlock the private key for the user [COLOR=#ff0000]joe[/COLOR]
...
gpg: encrypted with 2048-bite ELG-E-key, id ...
...
[COLOR=#008000]now I'm writing this (line 1)
and that (line 2)
and finish with ctrl + d (line 3)[/COLOR]
$

```

---

### Post by asteriks on 2013-03-04
hey, thank you sudodus, it works :)
great!

thanx and to you zero2xii, I know for cryptomx (for example), it has set of tools for encryption and conversion, but GPG is the best and of course, I am interested for GPG.
for example, if I succeed one day to educate myself for server admin, I will need to work from terminal and therefore I am trying to learn more to do from terminal. if graphic interface can do something, it means, there must be the way to do the same with terminal :) if software is installed, it must be possible. and sudodus showed us, it is possible :) thank you.

```

ubuntu@ubuntu:~$ **gpg -aer anyname**
**lets try this...**
-----BEGIN PGP MESSAGE-----
Version: GnuPG v1.4.11 (GNU/Linux)

hQIMA9NAIp1zLNwrAQ//XtqRh5TAXWTwnl4aJ0dNxPMzF9NTV39a9SxVbNe9v9yN
tV6R7cFAytk7d3tWX6lw1gHW/uJDHRnWLix/Yi6RUcRzbccxYMN2SanPKJpQ/Krn
SwGsrKGodqLtFZRVC/arS2vzIrq70JRG+UD2ooxeMmnjOb93l7KDb/nxG0+72aYm
y9EcAOfqk/8FJIs/sptFl7WUPWbge/PBnCXWf8T2eULGx/uESv4OJyDhtwfZ2kaO
QlzRgtT5QuEwldUw1+HmQ6vCItD21EgB6d7u0a0EPQG+YyZpuPvKmihRh0Y9y5yQ
WVPh46BfFLRnHm501iFnT7HTw+MozW+Sy7nDOOoM1j19AcxoU/iTduApYvC6tj5D
spVoe5EgcQkc+G9Z58l/zxOyySWx8Kgl++b8fI5n05yLYbz/Gv6jjGgZ8hiNslIw
tDgSQn19ceXbY08oG9BUYlfJkwkPO+GUiGVA7xYSPmeGU1mhININsjFVwFR0pWen
6Iyr2A+Jitkz1rvUDooxwOwn/9DewD7bUp7bYm6wfgNHAsUPV9+DrvJwZ4zhtVLk
Aw71BLVWCIVVgqMPCmCO8RqY+u2xMFnozUJf3cvg32hKRjnlEGCvz0qcu/mOxe9I
SIMBX6EYc/QTiR0lZyIRrgWEA73q4r+oHpV8HHVaRJ92B6XHlq2XeV2s/ZMVaPDS
TAFjVlHn5qZJnfePdZGt5rCxBf5av0YfmmMyXYWlB4Pg9cTunD9YnHBQ30uOPkcX
1EhWjDJP8Nfw3B1wwMNISZhca9ySzZKggfJUusc=
=YrHi
-----END PGP MESSAGE-----
ubuntu@ubuntu:~$ **gpg -d**
-----BEGIN PGP MESSAGE-----
Version: GnuPG v1.4.11 (GNU/Linux)

hQIMA9NAIp1zLNwrAQ//XtqRh5TAXWTwnl4aJ0dNxPMzF9NTV39a9SxVbNe9v9yN
tV6R7cFAytk7d3tWX6lw1gHW/uJDHRnWLix/Yi6RUcRzbccxYMN2SanPKJpQ/Krn
SwGsrKGodqLtFZRVC/arS2vzIrq70JRG+UD2ooxeMmnjOb93l7KDb/nxG0+72aYm
y9EcAOfqk/8FJIs/sptFl7WUPWbge/PBnCXWf8T2eULGx/uESv4OJyDhtwfZ2kaO
QlzRgtT5QuEwldUw1+HmQ6vCItD21EgB6d7u0a0EPQG+YyZpuPvKmihRh0Y9y5yQ
WVPh46BfFLRnHm501iFnT7HTw+MozW+Sy7nDOOoM1j19AcxoU/iTduApYvC6tj5D
spVoe5EgcQkc+G9Z58l/zxOyySWx8Kgl++b8fI5n05yLYbz/Gv6jjGgZ8hiNslIw
tDgSQn19ceXbY08oG9BUYlfJkwkPO+GUiGVA7xYSPmeGU1mhININsjFVwFR0pWen
6Iyr2A+Jitkz1rvUDooxwOwn/9DewD7bUp7bYm6wfgNHAsUPV9+DrvJwZ4zhtVLk
Aw71BLVWCIVVgqMPCmCO8RqY+u2xMFnozUJf3cvg32hKRjnlEGCvz0qcu/mOxe9I
SIMBX6EYc/QTiR0lZyIRrgWEA73q4r+oHpV8HHVaRJ92B6XHlq2XeV2s/ZMVaPDS
TAFjVlHn5qZJnfePdZGt5rCxBf5av0YfmmMyXYWlB4Pg9cTunD9YnHBQ30uOPkcX
1EhWjDJP8Nfw3B1wwMNISZhca9ySzZKggfJUusc=
=YrHi
-----END PGP MESSAGE-----

You need a passphrase to unlock the secret key for
user: "anyname <ola@ola.com>"
4096-bit RSA key, ID 732CDC2B, created 2013-03-04 (main key ID B23AA331)

gpg: encrypted with 4096-bit RSA key, ID 732CDC2B, created 2013-03-04
      "anyname <ola@ola.com>"
**lets try this...**
ubuntu@ubuntu:~$ 

```

---

### Post by sudodus on 2013-03-04
You are welcome :-)

and good luck with the command line!

[[COLOR=#ff0000]https://help.ubuntu.com/community/CommandLineResources[/COLOR]]("https://help.ubuntu.com/community/CommandLineResources")

---

### Post by JDial on 2013-04-20
command line is nice for gpg.  If you are going to be doing much on the command line it might be worth it to write a bash script using xclip.. I wrote a couple for my X apps that help with signing, verifying and importing keys and setup a keyboard shortcut to make life easier:

#!/bin/bash
PASS=$(zenity --password --title="GnuPG")
DATA=$(xclip -o)
echo $DATA"\n" | gpg --passphrase "$PASS" --clearsign --armor --batch | xclip -selection clip

and

#!/bin/bash
xclip -o | gpg &> /tmp/tmp.gpg_verify
zenity --width=800 --height=600 --title="GnuPG" --text-info --filename=/tmp/tmp.gpg_verify
rm /tmp/tmp.gpg_verify

pretty simple script, but they work

---

