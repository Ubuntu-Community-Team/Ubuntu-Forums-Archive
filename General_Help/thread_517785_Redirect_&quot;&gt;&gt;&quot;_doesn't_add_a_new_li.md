---
title: "Redirect &quot;&gt;&gt;&quot; doesn't add a new line??"
date: 2007-08-05
forum: General Help
---

### Post by kpictjl on 2007-08-05
I'm trying to add public keys to my .ssh/authorized_keys file and I'm running into what should be a fundamental *nix capability question.  When I do the command to add an additional public key
```
cat publickeyfile >> ~/.ssh/authorized_keys
```
for some reason this is not adding the new key to a NEW line.  ssh needs each public key to be on it's own line.  I am able to edit the authorized_keys file and add the new line, but I shouldn't have to.

When I test the ">>" tools on other files, it does add a new line.

Here is what I'm talking about, in the example below note that the "ssh-rsa" in the middle should be proceeded by a newline.
```

>:~$ rm .ssh/authorized_keys
>:~$ cat mypublic-key-joe >> .ssh/authorized_keys
>:~$ cat mypublic-key-jane >> .ssh/authorized_keys
>:~$ more .ssh/authorized_keys
ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAIBap2yfSxZWU+dhR2A6VnmSCnYCLl4BoE0O+FXIQxvmF1HY
U1UNQWwnGUrH4+WoXKnYty/gTJld8BLve2MsYlI5x4qGiAnYuHKf5zfzXZktJiYLuk+/Nx5lVjvB8S/c
PDDnCsQuPwwXsy/Jrjg9b9AvYYkPbPI1Z0c3Kbjn1dt5fw== rsa-key-20070802=created on
 2 Aug 07ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAIEAkRkcYBstUSLFpyLR6paVEwD92TXwBTq3iqr
3BL2KMYLSf5w8VrDWpAGV16i5nkI71wMrzN1HjzkaLUWv2C8UZueLLQ5nVaZKhCZGFLJPNMa4KxwrKkk
dJQ7tAeyZwNj78qEE0NjNkVAJvk1Ob7cEANHv/8KmQvII8ChuZA2NgMU= rsa-key-20070804
>:~$

```


I've test this using more simple characters and it works like I think it should (meaning it adds the new line)
```

>:~$ echo tttt > t
>:~$ echo uuuu > u
>:~$ cat t >> test
>:~$ more test
tttt
>:~$ cat u >> test
>:~$ more test
tttt
uuuu
>:~$

```

Am I using ">>" incorrectly or something?  Thanks.

---

### Post by nick_h on 2007-08-05
*cat* will not add a newline for you.  *echo* will add a newline unless you use the -n option.

You could use:
```
echo '' >> file.txt
```
to add a newline.

---

### Post by kpictjl on 2007-08-05
> **nick_h said:**
> *cat* will not add a newline for you.

How come my test in the original post does get a newline between tttt and uuuu?

---

### Post by walkerk on 2007-08-05
you can try using tee with the -a (append option):
```
echo 'what you have to say' | tee -a /path/to/file
```

---

### Post by nick_h on 2007-08-05
Your test uses echo without the -n option so that adds the newlines.  Your key files do not contain newlines.

Try:
```
echo -n tttt > t
echo -n uuuu > u
cat t >> test
cat u >> test
more test
```
If the input files do not contain a newline *cat* will not add one.

---

### Post by kpictjl on 2007-08-05
> **nick_h said:**
> Your test uses echo without the -n option so that adds the newlines.  Your key files do not contain newlines.

Try:
```
echo -n tttt > t
echo -n uuuu > u
cat t >> test
cat u >> test
more test
```
If the input files do not contain a newline *cat* will not add one.

Ahhh. I get it.  I hate it when I get tunnel vision like that.

Now thinking back to my original problem.  I guess my key files didn't have new lines in them due to the way I was copying them to the linux box.  I was cutting and pasting from the puttygen gui into a notepad document.  I could have inserted a carriage return there and been fine....I think.

Thank you for the help.

---

### Post by kpictjl on 2007-08-05
> **walkerk said:**
> you can try using tee with the -a (append option):
```
echo 'what you have to say' | tee -a /path/to/file
```

this works to, thanks!

I think the echo -n is a little more slick, but I've never heard of the tee command before.  This is great!

---

