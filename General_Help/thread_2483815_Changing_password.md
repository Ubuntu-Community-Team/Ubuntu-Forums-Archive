---
title: "Changing password?"
date: 2023-02-09
forum: General Help
---

### Post by garyed on 2023-02-09
I just upgraded to Ubuntu 22.04 & I decided I want to change my password.
Before I do so I wanted to check here to make sure I don't lock myself out of anything.
The only two users are myself & my wife & I don't want to change her password. 
I want to change the sudo password which I assume is the same as mine since that was the original password used during install.
My user name is Gary so my question is which command should I use if any to change my password & the sudo password.   
```
sudo passwd Gary
```
or
```
sudo passwd root
```

Any help appreciated

---

### Post by TheFu on 2023-02-09
a) usernames **need** to be lowercase.  Fix that first.  Mixed case usernames have all sorts of failure issues that cannot be pre-determined across the world of software.

b) individual users can change their passwords at any time by using 'passwd' without any arguments.  This is the preferred method.


There's no such thing as a "sudo password".   It is the same password as the user has.   Whether any user can use sudo or not is usually enabled by membership in the 'sudo' group.  Use 'id' to see what groups your username is a member.  between 2 and 5 is common, but some users in a corporate environment may have as many as 30 groups.

You should not use the 2nd command with 'root' in the line.  That opens the system to all sorts of security issues that are best avoided.

---

### Post by garyed on 2023-02-09
I stand corrected because my username is all lower case (gary).
So am I correct that if I do:  sudo passwd gary    
it should let me change my password & let me keep the root privileges I had before by using sudo & the new password ?

---

### Post by TheFu on 2023-02-09
> **garyed said:**
> I stand corrected because my username is all lower case (gary).
So am I correct that if I do:  sudo passwd gary    
it should let me change my password & let me keep the root privileges I had before by using sudo & the new password ?

Well, yes, but if you are logged in as 'gary', there's no difference in that command and running 'passwd' alone.

Just use
```
$ passwd
```

that's it for the current user.  If you are gary and want to change nancy's passwd ... well, there are multiple ways, like modifying the PAM settings to force her to change her password at the next connection, but she'll be made about that. You could claim, it was a system default.  With PAM, you can force password changes every X days and force complexities and prevent most trivial password patterns from being allowed, like humans are known to do ... say "pass$word02" --->  "pass$word05" when forced to change it again in May.  If you don't have good reason and passwords are never reused ( login passwords should never be used for email and those should never be used for any other online accounts) I'd say to have passwords expire every 1.5 yrs or so.  I also engineer it so expiring passwords happen on Tuesdays to everyone is back from the weekend and will have a few days to get used to the new password, assuming normal system locking happens after 15 min of inactivity in the environment.  Most of my remote connects are via keys these days.  Passwords are considered a failure in security in most enterprises.  Using a security FOB and a password is very common. While that FOB is pulled in and the local account is authenticated, authenticating to other systems doesn't need more than a finger touch on the FOB for that userid.  That's the dream, anyways.

Of course, no external accounts should know anything about each other or internal accounts.

---

### Post by garyed on 2023-02-09
Thanks for the help,
I think I've got it now. I'm just a little nervous because I've never changed my password before & I'm taking my laptop on a trip in the morning.
I wanted to have a more secure password on my laptop but I didn't want to mess things up where it might take two days to fix.

---

### Post by TheFu on 2023-02-09
Well, you should spend the time making a backup, doing a fresh OS load, then restoring **only** the stuff you need specifically for the trip.  Leave the backup at home.  Also, if it is a laptop, when you do a fresh install, use whole device encryption, like LUKS.  Using encryption means we need excellent backups.  No choice about that.

But really this stuff should have been done a few weeks ago, before it was last minute.

---

### Post by garyed on 2023-02-09
I know I should not have waited till the last minute to do this but I just got the idea last night to make a stronger password. 
There's not much sensitive data that I'm worried about on the laptop so I never worried much about security before. 
Encryption is probably the only truly safe way to make a laptop secure but I don't think I would trust myself with whole device encryption. 
I'm getting a little senile so I'd be worried about forgetting or losing the password :)

---

### Post by Dennis N on 2023-02-09
Another way is to go to Settings > Users
Unlock the dialog.
You can then change the user Password and/or User Name

---

### Post by TheFu on 2023-02-09
> **garyed said:**
> I know I should not have waited till the last minute to do this but I just got the idea last night to make a stronger password. 
There's not much sensitive data that I'm worried about on the laptop so I never worried much about security before. 
Encryption is probably the only truly safe way to make a laptop secure but I don't think I would trust myself with whole device encryption. 
I'm getting a little senile so I'd be worried about forgetting or losing the password :)

Split your passwords into 2 parts.

a) 10 characters that you never tell anyone and memorize.

b) 10 characters that are written down for each login, all random, never shared.  Keep this 2nd group in your wallet and treat it at least as securely as you would treat a debit/credit card without any contractual protections against loss.

For passwords you have to physically type, that's to access a computer, say I memorize "ClaptonSH" ... and reuse that for my passwords.
Then say I have a notepad with: 
* computer - {username0} - 1c138acad553a0
* password manager - 53d2b7123e

So, let's say my local login account to my laptop is thefu, then to login I'd need 
  username: thefu
  password: ClaptonSH#1c138acad553a0

Simple, secure and I'd only need to change the 2nd half as long as nobody new my super-secret first half.
Do this only for systems you have to physically touch.  That's probably a phone/tablet, desktop (home/work), laptop (home/work) and perhaps to unlock encryption to access storage.  No more than 5 things, probably.  One of those things is to access your password manager, right?  Use a very strong passphrase and perhaps either a yubikey FOB or an image as a keyfile to unlock the password DB.

For online accounts like email, google, banks, brokers, shopping ... all those need unique usernames and 100% random, long, passphrases that you don't know and don't need to know.  I can't tell you anything about my credentials for my retirement or brokerage accounts, except that I don't know them and don't even know the userid, which I setup to be random too.  Without the password manager and my investment account provided SSO device, there's no way I can login without talking to a human at the firm and them asking me some very specific questions, which I probably don't know the answers to either.  You know those "security questions?"  I make up answers that would never fit.  In short, I lie.  Nobody needs to know my mother's maiden name ... and it wouldn't do any good anyways.  For that security question I've probably provided a different 20 character random answer to each account.  Same for my first pet or high school mascot.  All random answers.

For internet logins, there isn't much we can do besides use 2FA that each sight supports.  Many are supporting FIDO2's u2f standard.  So having a device that supports that and can be used by all your devices (computers, tablets, phones) where you want to login, would be smart.  My tablets and phones don't know anything about my financial accounts.  My tablet doesn't have any email access at all - except what the provider setup as a way to get unimportant files to the device - like epub books.  I don't use phones or tablets for anything connected to money/buying/spending.  I've been to too many security conferences and seen how to hack android or iOS too many times to trust either.

Anyway, you have 2 methods.  
If you have to physically touch the device to login, use the 2-part password method.
If you only need network access to login, use a good password manager that can be trusted. Have all logins use different credentials (username/passphrase), use 2FA for things with money/buying/spending and even have different email addressed connected to the accounts based on the risks.  

For example, the email address I use here is the one I use for social stuff, but never for purchases or banking.  For banking, I have a separate email that is only used by the bank.  A different email is used for each investment company.   For the online retail stores we frequently purchase stuff from, those have unique email addresses too.  This makes it harder for scammers.  If I see a message claiming to be from amazon, but it isn't sent to my random amazon email address, then I know it is a scam and to ignore it.  This works for other accounts too.  I give out an email address to friendly acquaintances that is very different from the email address I give to family and close friends.  Most email providers will allow you to have 5 addresses and if you learn to use the [email]email+subject@domain.com[/email] method, you can have nearly infinite email aliases that would come to a single mailbox, but have different "TO:" addressing for filters. Not all email systems support this mode, so test it before you start using it.

I've probably said too much.

---

### Post by garyed on 2023-02-09
Well changing the password could not have been any easier so thanks again.
Just ```
 passwd gary 
```   did the trick.

---

### Post by TheFu on 2023-02-09
> **garyed said:**
> Well changing the password could not have been any easier so thanks again.
Just ```
 gary passwd 
```   did the trick.

Just to clarify ... the above cmd won't work.  The order is wrong.  There's no command "gary".

```
passwd gary
```  
and 
```
passwd
```  
are exactly the same.

The manpage for passwd, is pretty clear:
```
NAME
       passwd - change user password

SYNOPSIS
       passwd [options] [LOGIN]

DESCRIPTION
       The passwd command changes passwords for user accounts. [b]A normal user may
       only change the password for their own account[/b], while the superuser may
       change the password for any account.  passwd also changes the account or
       associated password validity period.

```

They synopsis above says that options and even the login are optional, as I tried to say clearly.

Regardless, glad you found the easy solution AND really happy you marked this thread as solved to help others in the community. Much appreciated.

---

### Post by #&amp;thj^% on 2023-02-09
> **TheFu said:**
> Just to clarify ... the above cmd won't work.  The order is wrong.  There's no command "gary".

```
passwd gary
```  
and 
```
passwd
```  
are exactly the same.

The manpage for passwd, is pretty clear:
```
NAME
       passwd - change user password

SYNOPSIS
       passwd [options] [LOGIN]

DESCRIPTION
       The passwd command changes passwords for user accounts. [b]A normal user may
       only change the password for their own account[/b], while the superuser may
       change the password for any account.  passwd also changes the account or
       associated password validity period.

```

They synopsis above says that options and even the login are optional, as I tried to say clearly.

Regardless, glad you found the easy solution AND really happy you marked this thread as solved to help others in the community. Much appreciated.
+1
I'm very glad you stepped in and wrote the correct procedure. Just for clarity for other users, thumbs up...
```
me passwd
me: command not found


```

---

### Post by garyed on 2023-02-09
> **TheFu said:**
> Just to clarify ... the above cmd won't work.  The order is wrong.  There's no command "gary".

```
passwd gary
```  
and 
```
passwd
```  
are exactly the same.

The manpage for passwd, is pretty clear:
```
NAME
       passwd - change user password

SYNOPSIS
       passwd [options] [LOGIN]

DESCRIPTION
       The passwd command changes passwords for user accounts. [b]A normal user may
       only change the password for their own account[/b], while the superuser may
       change the password for any account.  passwd also changes the account or
       associated password validity period.

```

They synopsis above says that options and even the login are optional, as I tried to say clearly.

Regardless, glad you found the easy solution AND really happy you marked this thread as solved to help others in the community. Much appreciated.

Sorry, thanks for catching that. I typed the command backwards in my post but I did actually execute the command: ```
 passwd gary 
``` & it worked fine. 
I just edited my other post to make sure nobody makes the same mistake that I did by typing the command backwards.

---

