---
title: "Password Manager KeePassXC"
date: 2019-06-01
forum: General Help
---

### Post by electrosteam on 2019-06-01
Lubuntu 18.04.2,
Gigabyte MoBo from 2005.

System running fine, now time to try a Password Manager, selected KeePassXC as a first attempt.
Did some searching, but help thin for advice on setting up initially.

Some really basic queries:
- is there a help document somewhere that would answer queries like these ?
 - what is a sensible location for the database ?
 - is it sensible to have a shortcut link to the database on the Desktop ?
 - should I keep a csv copy of the database raw text data on an external USB ?
 - integration with the browser ?
      - I am happy with accessing the database and clicking on the URL,
 - let the manager generate the passwords ?

There are probably other very obvious queries I should make, reflecting my total ignorance in this area.

Thanks in advance,
John

---

### Post by kpatz on 2019-06-01
1.  You could read the documentation and FAQ on the KeePassXC website to get answers.
2.  You can put the database wherever you like, but in a folder under your $HOME is best.  If you want to sync it with other computers, like Windows systems, put it in a folder shared by Samba to make it easy to get to.  Definitely keep backups of your database though, on different devices or computers, just in case.
3.  This is up to you.  I use KeePass2 and I just have it docked/favorited in my taskbar.  It remembers what database I opened last and opens it next time by default.
4.  I don't recommend keeping unencrypted copies of your passwords, but if it gives you peace of mind (in case you lose your database or passphrase), you can do this.  Just keep it locked away.
5.  There are browser plugins for the major browsers to allow for integration and auto-fill of credentials.
6.  For any password that I can copy/paste or autofill, I let the manager generate a strong random password with upper, lower, numbers, and symbols as long as the site accepts.  For my login password, KeePass passphrase, and any other password I have to **type** and not copy/paste, I use something I can remember and type easily, but I still use a mix of upper, lower, numbers and symbols.

Since you're just starting out with using a password manager, start simple.  Put your existing passwords in it for now.  Then, over time, as you get more comfortable with it and you have auto-fill working the way you want, you can start changing passwords on each site to a strong random password, since you won't have to memorize or type it.

---

### Post by VMC on 2019-06-01
I keep my keepass on a microsd card that I can plug in or leave in. I don't want that info on my hd or on the cloud.
I have a hard copy of the cvs file on a desk. Its older and I find using a password isn't much trouble.
Both chrome/firefox have password managers that can be as strong as you make it.

---

### Post by HermanAB on 2019-06-02
The password database is encrypted.  You can keep it anywhere.  Google docs, Dropbox or your own file server is convenient to access from any device.

---

### Post by TheFu on 2019-06-02
I've been using KeePassX and KeePassXC for a very long time.

I mirror the passwd DB nightly from my main desktop to about 6 other systems using rsync.  In my mind, I make updates only on my desktop, but use it as read-only on all the other platforms. This simplifies rsync, since that is a 1-way copy.  I've heard of people using file-sync tools like dropbox, owncloud, nextcloud, seafile, .... to have the replication of the DB automatic.  I prefer to have it happen only once a day, at a specific time (just after midnight), so if I make any mistakes, I can pull the file from either another system or versioned backup.

I do not keep a text version of the data.  Just ensure you have backups and keep the DB on multiple systems.

Always use a non-trivial passphrase to unlock the DB. After all, this is the "*keys to the kingdom*."
I use keepassxc for storing all sorts of things, not just login credentials.  [https://blog.jdpfu.com/2011/03/25/101-uses-for-a-password-manager](https://blog.jdpfu.com/2011/03/25/101-uses-for-a-password-manager)

I do NOT use browser integrations with password managers.  Browsers are extremely complex and they are full of bugs. Incognito modes have been known to fail.  Addons have been known to steal information from within the different browser sandboxes.  I simply don't trust them.

I want the entry of my credentials never to be automatic.  I want to always have some positive action on my part for a login to happen.

I almost always have KeePassXC generate long, complex, passwords for me.  55+ characters, since I'll never type them in.  There are a few exceptions, mainly due to web-apps that don't support long, complex, passwords.  Oddly, my bank limits passwords to 12 characters and only allows alpha-numeric characters.  To combat their poor password mandate, I changed my login to be 40 random characters.  I couldn't tell you my banking credentials.  The password is random, within their stupid limitations.  My other financial accounts use long, complex, passwords and a 2-factor authentication device, which they provided.  The number on the FOB changes every 60 seconds.

I also use U2F USB security devices for web-apps where I can.  This is in addition to the userid, password parts.  I've been using Yubikey devices about 5 yrs, where it makes sense.  My personal Nextcloud install can use U2F as well, but none of my Android devices work with it, so after playing with it a few hours, seeing that everything worked from desktops, I had to turn it off.

If you are interested in being secure, don't use the same email address for sensitive accounts.  Use a unique email address for your bank, a different one for your broker, and a different one for your retirement account(s).  
Never mix financial email addresses with social networks or  online retail email addresses.  
I use a different email alias for each online retailer too.  This makes it easy to see which retailer sold my information without my approval.  For the retailers, aliases are fine.

For those few passwords that need to be typed, use a system.  It is fine to have them written down, just don't have the entire password written down, just put some part of it on the paper, card, note, in your wallet, but use some phrase that only you know to prepend/append to whatever is on the note.

```
desktop = sdwer9;(&e w4ds
gmailA = 66e1$(!411 346e 
Protonmail = Tviu 7Ouvvub*$) 0pr
XC = ...[]iohykqe3eZk
```

I like using spaces in passwords. ;)

Then append that *known-only-to-you* part to finish off the password. These are for just those few accounts where you must, absolutely must, type in the password.  BTW, gmail supports u2f. Use it if you can.

---

