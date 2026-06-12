---
title: "GAIM not secure...how do i make it secure?"
date: 2007-01-20
forum: General Help
---

### Post by rekahsoft on 2007-01-20
Hi all, i was just looking at GAIM and found that it stores passwords in PLAIN TEXT in a xml configuration file. WTF is this? To get access of it all you have to do is a simple one line command:```
cat ~/.gaim/accounts.xml | grep password
```Is there an option that lets me change this crappy functionality? I know some people will argue that access to the file is limited to certain users but this could cause a problem for new users.

---

### Post by pay on 2007-01-20
Theres an addon to Gaim called Gaim encryption. Though I'm not sure what exactly it encrypts. [http://gaim-encryption.sourceforge.net/](http://gaim-encryption.sourceforge.net/)

Okay, I tested this and the password is only shown in that file if you tick remember password. So you might want to uncheck that.

---

### Post by SyvanX on 2007-01-21
wow, that's interesting.  Are its permissions set to 600?  That would at least keep it private, I'm not at my Ubuntu box right now, but I may have screwed with my home directory permissions at some point.  

I looked up the gaim info on this
[http://gaim.sourceforge.net/plaintextpasswords.php](http://gaim.sourceforge.net/plaintextpasswords.php)

They say they don't plan to encrypt the file now or in the future since most messaging protocols use insecure passwords and they also recommend that an instant messaging password not be used anywhere else.

I think this is more of problem for a yahoo or google account where the instant messenger also serves as the email password.  At least it's only a local problem.  I'm definitely going to remove password storage as soon as possible.

---

### Post by imjustabill on 2007-01-21
All gaim-encryption does is allow you to encrypt messages, has nothing to do with passwords as far as I know. A quick ls -l on the accounts.xml shows its only readable by the owner of the file, so its fairly secure as is, though I must say encrypting them would be much safer.

---

### Post by SyvanX on 2007-01-21
gaim-encryption will encrypt conversations between two gaim instances of gaim set up for encrypted conversations.  It doesn't help with the passwords though.

I prefer [Off-the-Record]("http://www.cypherpunks.ca/otr/"), it's a little bit simpler to me.

---

### Post by sddfdds on 2007-01-21
[http://gaim.sourceforge.net/plaintextpasswords.php](http://gaim.sourceforge.net/plaintextpasswords.php)

edit: oops, didnt see it already linked above.

---

### Post by rekahsoft on 2007-01-21
ok i have wrote a script that makes GAIM secure (well...more secure). First off i will state the problems with the solution:
1. You have to have the console open
2. The file is plaintext during the time GAIM is running
Note: requires a gpg key

I am wondering if anybody knows how i would go about fixing #1...i know that number 2 would mean having to build a plugin for gaim and i currently do not know C++ well enough to do so.

Here is the simple script i wrote:```
#/bin/sh

gpg_key="your gpg key email"
arguments=

# Turns off the encryption
unsecure_game() {
	if [ ! -f ~/.gaim/accounts.xml ]; then
		if [ -f ~/.gaim/accounts.xml.gpg ]; then
			gpg --output ~/.gaim/accounts.xml --decrypt ~/.gaim/accounts.xml.gpg
			rm ~/.gaim/accounts.xml.gpg
		else
			echo "You encrypted account information has been lost!!"
			exit 0
		fi
	fi
}

# decrypts account information file
open_gaim() {
	if [ -f ~/.gaim/accounts.xml.gpg ]; then
		gpg --output ~/.gaim/accounts.xml --decrypt ~/.gaim/accounts.xml.gpg
	fi
	gaim $arguments
}

# encrypts account information file
close_gaim() {
	if [ ! -f ~/.gaim/accounts.xml.gpg ]; then
		gpg --output ~/.gaim/accounts.xml.gpg --encrypt --recipient $gpg_key ~/.gaim/accounts.xml
	fi
	rm ~/.gaim/accounts.xml
}

while [ "$1" != "" ]; do
	arguments=$arguments" "$1
	shift
done

open_gaim
close_gaim
exit 0
```
Before trying this out make sure you back-up ~/.gaim/accounts.xml

---

### Post by ScottMorris on 2007-01-21
> **rekahsoft said:**
> ok i have wrote a script that makes GAIM secure (well...more secure). First off i will state the problems with the solution:
1. You have to have the console open
2. The file is plaintext during the time GAIM is running
Note: requires a gpg key

I am wondering if anybody knows how i would go about fixing #1...i know that number 2 would mean having to build a plugin for gaim and i currently do not know C++ well enough to do so.

Here is the simple script i wrote:```
#/bin/sh

gpg_key="your gpg key email"
arguments=

# Turns off the encryption
unsecure_game() {
	if [ ! -f ~/.gaim/accounts.xml ]; then
		if [ -f ~/.gaim/accounts.xml.gpg ]; then
			gpg --output ~/.gaim/accounts.xml --decrypt ~/.gaim/accounts.xml.gpg
			rm ~/.gaim/accounts.xml.gpg
		else
			echo "You encrypted account information has been lost!!"
			exit 0
		fi
	fi
}

# decrypts account information file
open_gaim() {
	if [ -f ~/.gaim/accounts.xml.gpg ]; then
		gpg --output ~/.gaim/accounts.xml --decrypt ~/.gaim/accounts.xml.gpg
	fi
	gaim $arguments
}

# encrypts account information file
close_gaim() {
	if [ ! -f ~/.gaim/accounts.xml.gpg ]; then
		gpg --output ~/.gaim/accounts.xml.gpg --encrypt --recipient $gpg_key ~/.gaim/accounts.xml
	fi
	rm ~/.gaim/accounts.xml
}

while [ "$1" != "" ]; do
	arguments=$arguments" "$1
	shift
done

open_gaim
close_gaim
exit 0
```
Before trying this out make sure you back-up ~/.gaim/accounts.xml
Cool, I may try this :P

Nice work!

---

### Post by imjustabill on 2007-01-22
> **rekahsoft said:**
> 
I am wondering if anybody knows how i would go about fixing #1...


I'm not sure if it would work as I'm not at my computer right now, but you could probably try this:

[LIST=1]
[*]Rename your gaim executable (I think it's in /usr/bin) to gaim-exe or something
[*]Edit your script to reflect the name change
[*]Save your script as "gaim" (without quotes) and put in in your $PATH
[/LIST]

This way, anything that invokes Gaim will just call the decryptor script first.

---

### Post by rekahsoft on 2007-01-22
> **imjustabill said:**
> I'm not sure if it would work as I'm not at my computer right now, but you could probably try this:

[LIST=1]
[*]Rename your gaim executable (I think it's in /usr/bin) to gaim-exe or something
[*]Edit your script to reflect the name change
[*]Save your script as "gaim" (without quotes) and put in in your $PATH
[/LIST]

This way, anything that invokes Gaim will just call the decryptor script first.

That would not work because the user has to enter a password for gpg to decrypt the gaim configuration file.

---

### Post by SyvanX on 2007-01-24
This seems like a lot of unnecessary work, unless you have an obscene amount of IM accounts.  If you're going to be entering a gpg password, why not just tell Gaim to not remember your IM passwords? 

chmod 600 is reasonably secure, an attacker needs access to your hard-drive or your root / user account to access the file.

I see this as more of a problem for Windows based systems with poor file permissions.

---

### Post by rekahsoft on 2007-01-24
> **SyvanX said:**
> This seems like a lot of unnecessary work, unless you have an obscene amount of IM accounts.  If you're going to be entering a gpg password, why not just tell Gaim to not remember your IM passwords? 

chmod 600 is reasonably secure, an attacker needs access to your hard-drive or your root / user account to access the file.

I see this as more of a problem for Windows based systems with poor file permissions.

True, i was just looking for a solution that would not require to disable remember password in GAIM.

---

### Post by LenzM on 2007-01-24
> **rekahsoft said:**
> True, i was just looking for a solution that would not require to disable remember password in GAIM.

What's the difference between entering a password in gaim rather than on the command line?

---

### Post by rekahsoft on 2007-01-24
> **LenzM said:**
> What's the difference between entering a password in gaim rather than on the command line?

Well, i have multiple accounts and do not want to have to type in a bunch of passwords everytime i start GAIM ;)

---

