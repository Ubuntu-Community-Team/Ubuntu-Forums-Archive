---
title: "Seahorse, Openpgp, Thunderbird &amp; enigmail ..."
date: 2013-07-19
forum: General Help
---

### Post by ELMIT on 2013-07-19
With seahorse I have created a new key for me of the type PGP key (for email encryption)

I verified it by checking properties of that key. It exists, is signed, has the right date, ...

Now I go to Thunderbird 17.07 on my AMD/64 machine and open Keymanagement under OpenPGP. No key is available!
I check the directory .gnupg and find an update of the pubring and secring according to the time I made the key.

I try to send a message to myself and get:   
Send operation aborted.
Error - encryption command failed


What do I miss?

---

### Post by sudodus on 2013-07-19
I suggest that you start by checking, that you can use the key from the command line, to encrypt and decrypt files.

See ```
man gpg
```

Start with the examples near the end of the man page:

```
EXAMPLES
       gpg -se -r Bob file
              sign and encrypt for user Bob

       gpg --clearsign file
              make a clear text signature

       gpg -sb file
              make a detached signature

       gpg -u 0x12345678 -sb file
              make a detached signature with the key 0x12345678

       gpg --list-keys user_ID
              show keys

       gpg --fingerprint user_ID
              show fingerprint

       gpg --verify pgpfile

       gpg --verify sigfile
              Verify the signature of the file but do not output the data. The second form is used for
              detached  signatures,  where  sigfile is the detached signature (either ASCII armored or
              binary) and are the signed data; if this is not given, the name of the file holding  the
              signed data is constructed by cutting off the extension (".asc" or ".sig") of sigfile or
              by asking the user for the filename.

```

---

### Post by ELMIT on 2013-07-19
Yes, from the command line it is working, ...

---

### Post by sudodus on 2013-07-19
I have Enigmail working in my Ubuntu 12.04 and Thunderbird. I installed it almost one year ago, and I remember it was a little tricky, but do not remember the details that well.

Read the tutorials you can find on the internet. And then go into all the menus of Enigmail (or associated to Enigmail) and try various options. For example, if you have several keys, on of them might be directly associated to your log in ID. It will probably be easiest to get that key working. You must get the password mechanism working.

---

### Post by ELMIT on 2013-07-19
I think I know where the problem is, but don't know how to solve it.

If I open Thunderbird and go to OpenPGP dropdown to Keymanagement, then there is not a single key.
It seems that it did  not get that the keys are in .gnupg

If I use the comandline then it gets the path to the keys and so it works. Where is in Thunderbird/Enigmail the path to the key?
I looked already in Thunderbird's  prefs.js  but could not spot it there.

---

### Post by sudodus on 2013-07-19
From [FONT=courier new]**man gpg**[/FONT]

       ```
--keyring file
              Add file to the current list of keyrings. If file begins with a tilde and a slash, these
              are  replaced  by  the  $HOME directory. If the filename does not contain a slash, it is
              assumed to be in the GnuPG home directory ("~/.gnupg" if --homedir or $GNUPGHOME is  not
              used).

              Note that this adds a keyring to the current list. If the intent is to use the specified
              keyring alone, use --keyring along with --no-default-keyring.
```

What is the OpenPGP 'settings' for the gpg path and options, for example at the 'advanced' tab?

---

### Post by ELMIT on 2013-07-19
Actually I don't really know what made it work, but it does now.

in Account settings:
I have removed old certificates I still had in the mail account settings from the time Thawte.
I have disabled/enabled in the account settings in OpenPGP Options (Enigmail) the key according to the email address
I ticked sign non-encrypted messages in account settings


in OpenPGP preferences
[Basic] I unticked Override with 
[Key Selection] I selected By rules and email addresses
  opened [Edit Rules] and clicked on [Add]
    added the email address in "Set OpenPGP Rules for"
    clicked on [Select Key(s)
    refresh key list and clicked the key I wanted (yeah, there the keys came up)


I think that was all I did, and now it is working!

---

### Post by sudodus on 2013-07-19
Congratulations :KS and thanks for sharing :-)

---

