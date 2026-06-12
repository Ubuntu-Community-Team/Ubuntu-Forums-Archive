---
title: "learning the command line: file streams other than #1 (stdout) and #2 (stderr)"
date: 2013-10-08
forum: General Help
---

### Post by sha1sum on 2013-10-08
First post, w00t,

Dear everyone. I'm learning to use the command line, just by playing with it and trying everything. So I have just learned that a command can put it's output on several numbered file streams. Standard output is #1 and standard error is #2, and you can redirect those when you write 1> and 2> respectively.

So now I was playing with the gpg command (my second favorite one) and I tried to redirect the output streams. When you decrypt something with gpg, it looks like this:

-------------------

You need a passphrase to unlock the secret key for
user: "Test key"
2048-bit RSA key, ID 8F94BA6A, created 2013-10-08 (main key ID 3ACEAA29)

[COLOR=#ff0000]gpg: encrypted with 2048-bit RSA key, ID 8F94BA6A, created 2013-10-08
      "Test key"[/COLOR]
[COLOR=#008000][THIS IS AN ENCRYPTED MESSAGE WRITTEN BY SHA1SUM][/COLOR]
[COLOR=#ff0000]gpg: Signature made Tue 08 Oct 2013 10:27:20 PM CEST using RSA key ID 3ACEAA29
gpg: Good signature from "Test key"[/COLOR]
-------------------

So I discovered that the decrypted message (green) is outputted as the standard output #1 and the red text as standard error #2. However, the command outputs more text which is neither stdout nor stderr. I was not able to redirect it with 1> and 2>

So, my questions are:
1) Are there other output streams apart from stdout and stderr
2) How do you redirect those (3> does not work...)

kind regards,
sha1sum

---

### Post by kvc2 on 2013-11-05
Hi there!

I had the exact same issue as you. So:

1) Are there other output streams apart from stdout and stderr
2) How do you redirect those (3> does not work...)

You can have as many streams as you want - and they can be numbered, or you can name them.  Check this out: [http://www.tldp.org/LDP/abs/html/io-redirection.html](http://www.tldp.org/LDP/abs/html/io-redirection.html)

HOWEVER - you need to know the name/number of the stream to redirect it!  I couldn't figure it out in the case of gpg.  However, I DID find that if you do "gpg --no-tty" it will suppress this text:

"You need a passphrase to unlock the secret key for
user: "Test key"
2048-bit RSA key, ID 8F94BA6A, created 2013-10-08 (main key ID 3ACEAA29)"

I realize that's not a perfect answer, but it met my needs and I hope it meets yours!

---

### Post by sha1sum on 2013-11-07
Thank you for your reply. Very good answer, I learned some new things. :D

---

