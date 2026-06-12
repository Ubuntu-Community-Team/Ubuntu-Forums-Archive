---
title: "How to determine number of encryption rounds on existing SSH key?"
date: 2021-12-30
forum: General Help
---

### Post by &amp;KyT$0P# on 2021-12-30
I have a SSH private/public key pair that was recovered from another machine.  I would like to generate another keypair using the same number of encryption rounds I used to make this one.  Unfortunately I don't remember what that number was, but I do know it was not the default.

How to determine the number of encryption rounds for this key?  That is, how to find out from the key files what value I passed to [FONT=Courier New]-a[/FONT] parameter of [FONT=Courier New]ssh-keygen[/FONT] when generating this key?

I do have the passphrase and can unlock this key with [FONT=Courier New]ssh-add[/FONT] , however the client machine being out of commission I am seeking a solution that doesn't involve making a SSH connection with this key.

---

### Post by &amp;KyT$0P# on 2022-01-03
bump

---

### Post by dragonfly41 on 2022-01-03
Well I did get as far as reading about the topic, out of curiosity. Perhaps you should post on bouncy castle forum for example.

[https://proandroiddev.com/security-best-practices-symmetric-encryption-with-aes-in-java-7616beaaade9](https://proandroiddev.com/security-best-practices-symmetric-encryption-with-aes-in-java-7616beaaade9)

[https://pretagteam.com/question/java-bouncy-castle-cryptography-encrypt-with-aes](https://pretagteam.com/question/java-bouncy-castle-cryptography-encrypt-with-aes)

---

### Post by &amp;KyT$0P# on 2022-01-03
Thanks for the reply dragonfly41.  I looked into bouncy castle and it looks like a module for Java programs.  So I would need to write my own program for this?  If so, I would be best able to write it in Python3, but since I couldn't find any existing Python module that does this, how to get the number of rounds after reading & base64-decoding the key file data?

---

### Post by &amp;KyT$0P# on 2022-01-06
bump

---

### Post by slooksterpsv on 2022-01-07
There's not actually a good way to determine how many "rounds" of encryption you've done. Otherwise, that would make it easier to guess what the key/passphrase is. Best bet would be to use a strong passphrase (more than 16 characters and include spaces). If you want to do additional encryption, I'd recommend bcrypt, you can specify how many iterations of encryption to perform. It works really well and the more iterations, the longer it takes to generate the encrypted value.

If you don't mind me asking, what is the SSH key used for? Is it for a connection to a computer/server your use? Is it used in some other application? Is there a reason you don't just increase the amount of rounds from what you previously thought you used?

---

### Post by &amp;KyT$0P# on 2022-01-07
> **slooksterpsv said:**
> There's not actually a good way to determine how many "rounds" of encryption you've done. Otherwise, that would make it easier to guess what the key/passphrase is.

But SSH determines it somehow when I provide the correct passphrase and unlock the key.  Does it not know how many rounds until I actually do provide the passphrase?

> If you don't mind me asking, what is the SSH key used for?

It was for SSH connection to another machine on the LAN.

> Is there a reason you don't just increase the amount of rounds from what you previously thought you used? 

I put some thought into the number and also did some rough benchmarking.  I would prefer not to repeat all that.

---

### Post by schragge on 2022-01-07
I found this: [The OpenSSH Private Key Format]("https://coolaj86.com/articles/the-openssh-private-key-format/"). The author couldn't find an official description, and resorted to reverse engineering the format from the source code. Ironically, the source includes [the description of the format]("https://github.com/openssh/openssh-portable/blob/master/PROTOCOL.key"). The number of rounds is included in what is called **kdf** at the former link or **kdfoptions** in the official description.

BTW, while it's implied that **kdfname** is [bcrypt]("https://en.wikipedia.org/wiki/Bcrypt"), it actually appears to be a tweaked version of bcrypt, [bcrypt_pbkdf]("https://flak.tedunangst.com/post/bcrypt-pbkdf"). Having been developed at OpenBSD, it uses [**O**xychromatic**B**lowfish**S**wat**D**ynamite]("https://github.com/openssh/openssh-portable/blob/dc38236ab6827dec575064cac65c8e7035768773/openbsd-compat/bcrypt_pbkdf.c#L77") as its [magic string](https://en.wikipedia.org/wiki/Nothing-up-my-sleeve_number) ;)

---

### Post by &amp;KyT$0P# on 2022-01-07
Thanks schragge, that pointed me in the right direction!  I looked at that format page but couldn't figure out how to write a parser myself.  In searching for help with parsing I happened on a solution: there is a software "openssh_key_parser" that can show number of rounds out of the box.  Installed it with
```
pip3 install openssh_key_parser
```
then ran
```
python3 -m openssh_key [COLOR="#FF0000"]<my_private_key>[/COLOR]
```
This prompted me for the private key passphrase.  After giving the correct passphrase it displayed a lot of data that included the number of rounds, which can be filtered by piping to [FONT=Courier New]grep -F rounds[/FONT]

Thanks again all for the replies! :KS

---

