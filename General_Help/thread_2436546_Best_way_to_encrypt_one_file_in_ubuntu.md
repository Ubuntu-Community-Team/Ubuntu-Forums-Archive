---
title: "Best way to encrypt one file in ubuntu"
date: 2020-02-08
forum: General Help
---

### Post by Tom_Carr on 2020-02-08
I want to create a txt file where I store all my passwords.  What is the best way to encrypt it?

---

### Post by oldfred on 2020-02-08
I use keepassX. No need to reinvent the wheel.
I was also able to email file to my iPhone and use it there also.

> KeePassX is a free/open-source password manager or safe which helps you
to manage your passwords in a secure way. You can put all your
passwords in one database, which is locked with one master key or a
key-disk.


---

### Post by TheFu on 2020-02-08
> **Tom_Carr said:**
> I want to create a txt file where I store all my passwords.  What is the best way to encrypt it?

Use a password manager that has a cross-platform DB like any of the keepass variants.  I like **KeePassXC** because it has fewer dependencies than some other options, there is a lite Windows version and Android versions.

Keeping passwords inside a text file is a liability since many tools will use temporary files that don't always get cleaned up between the encryption/decryption processes.

For anything other than passwords where I need to share the file(s) with other people, I'd use ZIP with a 55 character passphrase ... which I keep in my KeepassXC DB. ;)  Getting my accountant to encrypt files we  shared was a huge accomplishment for the security of my financial records.  ZIP passwords under 30 characters are prone to brute force attacks due to the way ZIP encryption was designed for efficiency.  Billions of ZIP passwords can be attempted every second.

Password DBs have all sorts of uses: [https://blog.jdpfu.com/2011/03/25/101-uses-for-a-password-manager](https://blog.jdpfu.com/2011/03/25/101-uses-for-a-password-manager)  I keep scans of my passport, immunization records, travel insurance, bank and other account numbers, software license keys, GPG keys, and all sorts of emergency data like immediate family contacts.  I know with just my password DB and nothing else, I can pretty much regain control of my life should a region-wide disaster hit.  Hook it up with either a key file or TOTP crypto-device combined with a passphrase for access and posting it all over (mine is on 6 different systems) ensures any storage or device failure doesn't lose that data.

---

### Post by Tom_Carr on 2020-02-08
I just learned that you can save Libre Office documents with a password.  I will probably use that for some things.  Does anyone know if  I save  a libre office document as a .doc file with a password, and then try to open it with MS Word, if the password  will work?

---

### Post by Tom_Carr on 2020-02-08
I don't see how to password protect a zip file.  If I right click on a file in file manage and then select compress I don't see any option to encrypt.

---

### Post by howefield on 2020-02-08
> **Tom_Carr said:**
> I don't see how to password protect a zip file.  If I right click on a file in file manage and then select compress I don't see any option to encrypt.

If you are not averse to using the terminal, you could try..

```
zip --encrypt destination_file source_file
```
 
eg, assuming a file called Additions in /home/user/Documents and zip is installed.

```
hugh@tumbleweed:~>  zip --encrypt /home/hugh/Documents/Additions.zip /home/hugh/Documents/Additions 
Enter password: 
Verify password: 
  adding: home/hugh/Documents/Additions (deflated 56%)
```

Or use the Archive Manager application..

[ATTACH=CONFIG]284987[/ATTACH]

---

### Post by Dennis N on 2020-02-08
You can encrypt from Files (Nautilus) if you install:

1) seahorse
and
2) seahorse-nautilus

You right-click on the file, and select "Encrypt.." Select "use passphrase" if you don't have a gpg public/private key pair. You can also select multiple files, or even a folder.

---

### Post by TheFu on 2020-02-08
> **Tom_Carr said:**
> I just learned that you can save Libre Office documents with a password.  I will probably use that for some things.  Does anyone know if  I save  a libre office document as a .doc file with a password, and then try to open it with MS Word, if the password  will work?

Hacking office documents is fairly trivial.  Don't store passwords in those.

Please, use a freakin' password manager.  There are reasons security people push them.

---

### Post by HermanAB on 2020-02-09
+100 for KeepassX

---

### Post by kurt18947 on 2020-02-09
There's another password manager that stores data locally - Enpass. Install the program and there's a Firefox extension. I'm tinkering with it. It's not open source if that matters.

---

### Post by mastablasta on 2020-02-10
i use Keepass2 - you can lock the passwords with password or with password + key (that you might want to put on separete USB key) for super strong encryption.

---

