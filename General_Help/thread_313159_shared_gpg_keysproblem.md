---
title: "shared gpg keys/problem???"
date: 2006-12-05
forum: General Help
---

### Post by RichJacot on 2006-12-05
I'm new to gpg and have been playing around trying to figure it out for a few days.  I have two machines and I have figured out how to encrypt one and decrypt it on the other and visa versa.  I can also encrypt and decrypt on the same machine.  HOWEVER, what I would really like to do is to encrypt on either machine and be able to decrypt on either machine.  The way I'm doing it, I'm only able to do it one way.  I.E. If I:

```
gpg -e -r <Key ID> somefile.txt
```

I can only decrypt it on the other machine, not the machine I encrypted it on.  The "Key ID" above is the key I imported from the other machine.  And yes, I have imported the keys from each machine.

Is there a way to do this that I haven't figured out, or am I dreaming?  (I do have full sudo on each machine)

Thanks,
Rich

---

### Post by defishguy on 2006-12-05
GPG uses something called public key encryption.  You actually create two keys when you set it up, one is public (to share with others) and one is private that you need to keep secret.  When you encrypt something to yourself, gpg encrypts to your public key and then uses your private key to decrypt it.  If you're using files encrypted to yourself then you need to use the same set of keys on each machine in order to do what you want.

Open a terminal and type

sudo apt-get install seahorse

When it finishes

hit <alt> <f2>

Type seahorse

You should see whatever public/private keys that you have created in the My Personal Keys tab.  Right click on the key and select export and save the file to whatever flash drive or floppy disk you choose.  On the second machine perform the same tasks only you'll be importing the keys instead of exporting them.

I assumed that both machines were running Ubuntu, your mileage may vary if you are crossing distros.  Warning... if you lose your private key by reformatting or some other activity you will not be able to recover the files unless you keep a backup copy of your keys in a very safe place.

Check out [http://www.pgpi.org/doc/pgpintro/](http://www.pgpi.org/doc/pgpintro/) when you get the chance.

---

