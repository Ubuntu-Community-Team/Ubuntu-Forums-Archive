---
title: "[SOLVED] import ssh key in seahorse??"
date: 2008-02-08
forum: General Help
---

### Post by seventhc on 2008-02-08
OK, I set up a second computer today and have copied both folders .gnupg and .ssh. When I open seahorse I can see my main key that would be used for email, and digital signatures, but the ssh key doesnt show up.
I still have access to the other computer, can someone please tell me what folder I need to copy over.
Thank you. :)

I also tried to back up the keyring from seahorse but when I tried to import that into the other machine it tells me it isn't a valid format (.asc)

---

### Post by seventhc on 2008-02-08
anyone??

---

### Post by seventhc on 2008-02-08
*bump*

---

### Post by p_quarles on 2008-02-08
The general guideline is to refrain from bumping a thread until at least 24 hours have passed. Be patient.

---

### Post by seventhc on 2008-02-08
I am patient, but I was just trying to get it to the top for any new people that log in. In 24 hours, the same people will be on if thats their normal time, and it would go unanswered, but this one is sort of important.

---

### Post by kevdog on 2008-02-09
Ive never used seahorse,  but on both computers when you type at the command line:
gpg --list-keys
gpg --list-secret-keys

Are the results the same?

---

### Post by seventhc on 2008-02-09
> **kevdog said:**
> Ive never used seahorse,  but on both computers when you type at the command line:
gpg --list-keys
gpg --list-secret-keys

Are the results the same?
Thanks for replying,
Yes they are the same...

---

### Post by kevdog on 2008-02-09
Ok it seems like the key rings are the same between the computers then.  The ssh key however is different than the gpg keys.  I believe the ssh keys are stored in the .ssh directory and known as id_rsa and id_rsa.pub.

---

### Post by seventhc on 2008-02-09
Thats part of the problem though, I copied the .ssh directory, but it doesn't show up on this computer. This is where my confusion is coming from, since I thought I copied everything I needed. (.gnupg, .ssh) Is there something else I'm supposed to copy??

---

### Post by seventhc on 2008-02-09
I wanted to explain, the .ssh dir shows up on the computer, just not in seahorse.

---

### Post by p_quarles on 2008-02-09
> **seventhc said:**
> I wanted to explain, the .ssh dir shows up on the computer, just not in seahorse.
What are the permissions on the ~/.ssh directory?

---

### Post by seventhc on 2008-02-09
I am listed as the owner, and it says I have access to it.

---

### Post by kevdog on 2008-02-09
So just to confirm.  The .ssh folder is located in ~
The .ssh folder is owned by you.

What are the permissions on the individual files within the folder?  Do they need to be made readable to group or others to work with seahorse?

---

### Post by p_quarles on 2008-02-09
> **seventhc said:**
> I am listed as the owner, and it says I have access to it.
Owner is one thing, but SSH keys need to have specific permissions settings (640 if I recall correctly).

---

### Post by seventhc on 2008-02-09
It is in my home folder,
the permissions read the same for both .ssh and .gnupg but should I try 
```
chmod 640 .ssh
```

---

### Post by p_quarles on 2008-02-09
Well, that couldn't hurt, but if I were you I'd try to rule that out as a problem first:
```
ls -l ~/.ssh
```

---

### Post by seventhc on 2008-02-09
I tried the chmod, but then it took away rights to run that command, set it to 755 and I get this
```

j0hn@cipher:~$ ls -l ~/.ssh
total 12
-rw-r--r-- 1 j0hn j0hn    0 2008-02-08 17:24 authorized_keys
-rw-rw-rw- 1 j0hn j0hn 3311 2008-02-08 17:24 id_rsa
-rw-rw-rw- 1 j0hn j0hn  725 2008-02-08 17:24 id_rsa.pub
-rw-rw-rw- 1 j0hn j0hn  724 2008-02-08 17:24 other_keys.seahorse

```

---

### Post by p_quarles on 2008-02-09
First off, I should correct myself: the right perms for the id_rsa key is 600. So, 
```
sudo chmod 600 ~/.ssh/id_rsa
```
Run that, log out and then back in, and try to connect again. I've never used seahorse, though, so this may not be enough to correct the problem.

---

### Post by seventhc on 2008-02-09
OK, I did that, now it reads as:
```

-rw-r--r-- 1 j0hn j0hn    0 2008-02-08 17:24 authorized_keys
-rw------- 1 j0hn j0hn 3311 2008-02-08 17:24 id_rsa
-rw-rw-rw- 1 j0hn j0hn  725 2008-02-08 17:24 id_rsa.pub
-rw-rw-rw- 1 j0hn j0hn  724 2008-02-08 17:24 other_keys.seahorse

```

Edit- I didn't see that you said to log out..doing that now.

---

### Post by p_quarles on 2008-02-09
> **seventhc said:**
> OK, I did that, now it reads as:
```

-rw-r--r-- 1 j0hn j0hn    0 2008-02-08 17:24 authorized_keys
-rw------- 1 j0hn j0hn 3311 2008-02-08 17:24 id_rsa
-rw-rw-rw- 1 j0hn j0hn  725 2008-02-08 17:24 id_rsa.pub
-rw-rw-rw- 1 j0hn j0hn  724 2008-02-08 17:24 other_keys.seahorse

```

Edit- I didn't see that you said to log out..doing that now.
Exactly as it should. Is it still not working?

---

### Post by seventhc on 2008-02-09
Still not showing in seahorse...I'm really at a loss, it seems as if everythng is as it should be. Other than the fact that seahorse doesn't detect it.:confused:

---

### Post by kevdog on 2008-02-09
Ive never used seahorse -- does seahorse keep a separate keyring other than the .ssh folder and gpg keyrings?  I took a look at the website, and it has options of importing keys.  Where does seahorse keep these keys??  It seems from looking at the developer page that seahorse may keep its own keyrings.

---

### Post by seventhc on 2008-02-09
The only folders that I know of are .gnupg and .ssh, I had what I thought was a backup with an .asc and it doesn't let me import it

---

### Post by kevdog on 2008-02-09
What happens when you try to import your private ssh key for example into seahorse -- I see this as an option in the seahorse screenshots.

---

### Post by seventhc on 2008-02-09
It tells me that its an invalid file format...
I did an export from the old, then tried to import on the new machine and  it says invalid.

---

### Post by kevdog on 2008-02-10
Do you know what format the program wants the keys in?   I couldnt find any documentation.  As far as .ssh keys, what other format do they want??  gpg keys can be exported as armor format, surely they dont expect this format!!

---

### Post by seventhc on 2008-02-10
I'm really not to sure what format they expect, but I would think having the .ssh folder would be a valid backup as is. As far as documentation goes, I really haven't found anything to useful yet.
The help file in seahorse is very limited, as is their documentation on their web site.

---

### Post by Herman on 2008-02-10
:) Hello seventhc and kevdog,
To back up my PGP keys in Seahorse, I opened Seahorse and went 'Key'-->'Back up KeyRings'
Name: keyring.tar.gz            (it must be given a name with an extension for some kind of archive file).

Copy the keyring.tar.gz to the other computer.
Right-click on it and 'Extract here'  the archive
'Edit'-->'Import', and navigate to the keyring folder. Make sure 'Show all Files' spinbox is set.
Select the file to import and click 'open'.

Shift-delete the key files when you are finished with them, for security reasons.

Now for the RSA keys for SSH.
In the old operating system I just opened my old /home/username directory and clicked 'Show hidden files'.
The I opened the .ssh directory and copied out the two RSA files, my private one is called  rd_rsa and my public one is called id_rsa.pub

Then, in the new operating system, do the same thing, open .ssh and paste in rd_rsa and id_rsa.pub
These should show up in Seahorse now.

Again, destroy any leftover copies for security reasons.

Regards, Herman :)

---

### Post by kevdog on 2008-02-10
So for pgp or gpg seahorse actually keeps its own internal keyring?  I see the method you posted for the ssh keys.  It was my understanding he did this method already but wasn't working!

---

### Post by seventhc on 2008-02-10
This is where my confusion comes in I have rd_rsa and id_rsa.pub in my .ssh folder, so this is why I don't understand why seahorse isn't seeing it.

I also just noticed something else that may be where my problem is coming from. I just went to see what options I get when generating a new pair, and ssh isn't even an option. I'm starting to think the problem may be something with seahorse, maybe it's corrupt or something...

---

### Post by Herman on 2008-02-10
Oh, shoot! I thought I was solving the problem for you.
Sorry for bothering you then. :oops:

Have you tried closing Seahorse and re-opening it, or even rebooting Ubuntu?
It should show up or something else is wrong there somewhere. 

Regards, Herman  :)

---

### Post by seventhc on 2008-02-10
Don't be sorry and you're not bothering me :) I appreciate all and any efforts. :)
I have closed/re-opened. logged out, back in...and rebooted. 
Honestly, I'm not sure if there is actually anything left to try. lol

---

### Post by Herman on 2008-02-10
I tried deleting my keys and importing them again from the command line to see if that would be any help to you, but that didn't even work for me very well.
Just in case you're interested, the commands I tried were 'sudo seahorse-tool -i id_rsa' and 'sudo seahorse-tool -i id_rsa.pub'.
Those didn't work unless I did 'cp id_rsa .ssh/' and 'cp id_rsa .ssh/' first, which proves nothing because it only achieves the same thing I was already able to do anyway.

I happened to use the ls-l command during the proceedings, and it has occurred to me that maybe you should check your file ownership and permissions for those rsa files.
Mine are both like: '- rw- --- --- 1 herman herman' which would be 'chmod 600' I think. 
Just a thought, maybe you should check, I have no idea how your file permissons might have been changed, it's a longshot, but things like that happen to me sometimes, especially when I use 'sudo' for things.
Did you change your username at all when you installed the new operating system? I'm clutching at straws.

Regards, Herman :)

---

### Post by kevdog on 2008-02-10
You ever get this problem solved?

---

### Post by seventhc on 2008-02-10
> You ever get this problem solved?no :(
I just tried to run the commands from above and it's telling me file not found, but the files are there...
Do you think using Hardy Heron could be the cause???
I really didn't think it should effect that but at this point it's the only rational thing that would make any sense to me. If that is the case, I'm sorry for wasting everyones time.
I have no real reason to reinstall, but just to test this out, I may put gutsy back on b/c none of this is  making any sense. I  mean the fact that this one thing seems all correct yet it isn't reading them, and even the command fails.

@Herman, I have checked the file permissions and they are set correctly.
Thanks to everyone for all the suggestions. :)

---

### Post by kevdog on 2008-02-10
Sorry I was unable to help you!:(

---

### Post by seventhc on 2008-02-10
> **kevdog said:**
> Sorry I was unable to help you!:(
I appreciate your efforts, I am starting to think there is no fix, I think it's just a glitch. I am going to reinstall Gutsy, and I think it will work. :)
Just not in the mood for a reinstall right now lol, in a day or 2 ;)

---

### Post by seventhc on 2008-02-14
OK solved, I'm so sorry I wasted your time. I installed Gutsy 7.10 tonight and now it works, I had no idea Hardy would be to blame. I did start to think that after trying everything, but now it is a fact.
Thank you everyone for trying to help me.
Now it is solved.
Should would I file a bug report on this?

---

### Post by kevdog on 2008-02-15
Those dang bugs - wouldn't have actually thought of blaming the problem on a distro bug or conflict--- I hate when things like this happen!!

---

### Post by seventhc on 2008-02-15
I know, it was hard to connect the two, and the only way was for me to install 7.10, but now we know. :)
The only thing I am unsure of is, how do I submit a bug report on this? I don't have any errors since I reinstalled.
Point to this thread maybe???
And if so where do I submit?

---

### Post by Herman on 2008-02-15
:) Hello seventhc and kevdog,
I'm typing to you right now from my new Hardy Herron installation. I installed Hardy Herron yesterday.  I used to have Feisty Fawn and Gutsy Gibbon in my laptop and now I have Gutsy Gibbon and Hardy Herron.  

I can't get my RSA keys for SSH to show up in Seahorse in Hardy Herron either.

I noticed something else about Hardy Herron too, there's no 'Connect to Server' in the 'Places' menu. I can make an SSH connection from the command line okay, but the  GUI method isn't ready yet I guess. Probably someone's working on it and it'll appear after an update with some improvements.
I'm not sure if the non-appearance of the RSA keys in Seahorse is worth reporting as a bug, my guess is it's just something that's not finished yet in Hardy Herron.

Regards, Herman :)

---

### Post by seventhc on 2008-02-15
I haven't reported it yet. :)
What you say makes sense, so we will wait and see. :)
But...I really wish I connected it to hardy earlier, myself, *kevdog* and *p_quarles* have put  lot of time trying to figure out what it was that I had done wrong. lol
But it wasn't me this time :cool:

---

### Post by kevdog on 2008-02-15
Just want to make sure if you do a gpg --list-keys that your RSA signing/encryption keys shows?   I use both RSA signing and encryption keys (rather than DSA/ElGamal).  I don't use seahorse however.  Hopefully I'll get around to Hardy soon, but will probably wait until its officially released.  Concerned with security myself, its not always good to be the first on the block to take the plunge in regards to security measures.

---

### Post by Herman on 2008-02-16
Okay, I tried 'gpg --list-keys', and it show me my public and private pgp keys, but it doesn't show my RSA kesy at all. I know the id_rsa and id_rsa.pub are both in my .SSH directory though.

I decided to try getting Seahorse to generate me some new RSA keys to see if those will show up in the 'gpg --list-keys' command output.
Guess what?
The option to generate RSA keys (for SSH) doesn't appear in Seahorse in Hardy Herron like it used to in Gutsy. :confused:

Regards, Herman :)

---

### Post by seventhc on 2008-02-16
If you open seahorse and hightlight the ssh key, click on properties, then the details tab, it shows that its RSA algorithm.

---

### Post by kevdog on 2008-02-16
RSA keys are shown if you do a gpg --list-keys.  Here is an example: (names omitted):

pub   4096R/7EBCE6DE 2007-11-14
uid                  name
uid                  [jpeg image of size 3122]
sub   4096R/E4193E1A 2008-02-15

pub   3072D/0053175A 2007-11-14
uid                 name
sub   4096g/51BFA0E0 2007-11-14

pub   4096R/80656AF7 2007-11-30
uid                  name
sub   4096R/A88E5D54 2007-11-30

Here is how to interpret the results.  The primary key is the signing key (pub).  Subkeys are the encryption keys.  3072 means a 3072 bit key whereas 4096 means a 4096 bit key

R = RSA
D = DSA
g = Elgamal

Again possible choices for a signing key are either DSA (D) or RSA (R).  Possible encryption algorithms for the encryption key are either El-Gamal (g) or RSA (R).  

I hope this is clear!?

---

### Post by Herman on 2008-02-16
Hey, that's really cool! Thanks for sharing that, kevdog!

Now I'm sure I'm only getting gpg keys in Hardy in the output from the gpg --list-keys command.
I'm happier to know how to read the output, that will come in handy from now on.

---

### Post by kevdog on 2008-02-17
Problem solved??

---

### Post by seventhc on 2008-02-17
> **kevdog said:**
> Problem solved??
If you mean the original problem, it got solved when I installed gutsy, now it shows as it is supposed to. So it must have somehow been related to Hardy 8.04.
Although when I do gpg --list-keys I do get a different out put

pub   1024D/12B0F063 2007-12-24 [expires: 2008-08-24]
uid                  <my name>
uid                  [jpeg image of size 3246]
sub   2048g/43321918 2007-12-24 [expires: 2008-06-24]

So I don't think it is showing as in yours, but it's there when I open seahorse.

---

### Post by kevdog on 2008-02-17
What do you mean your output is correct:
```


pub 1024D/12B0F063 2007-12-24 [expires: 2008-08-24]
uid <my name>
uid [jpeg image of size 3246]
sub 2048g/43321918 2007-12-24 [expires: 2008-06-24]

```

You have a 1024 bit DSA signing key and a 2048 El-Gamal Encryption Key.  Im not trying to plug my own thread here but I'm currently writing an advanced GnuPG tutorial.  Its a work in progress so its not really done, however it might (hopefully) give you more background on GnuPG.  I recommend the following two posts for reading (sorry if you know about these items:)

Basic Tutorial: [http://ubuntuforums.org/showthread.php?t=680292&highlight=gnupg](http://ubuntuforums.org/showthread.php?t=680292&highlight=gnupg)
Advanced Tutorial (work in progress): [http://ubuntuforums.org/showthread.php?t=687173&highlight=gnupg](http://ubuntuforums.org/showthread.php?t=687173&highlight=gnupg)

---

### Post by seventhc on 2008-02-17
Thanks, I'll give it a look. :)
I didn't mean mine was incorrect, but it isn't showing anything with 'R' for RSA. So I was thinking my ssh key isn't showing.

---

### Post by kevdog on 2008-02-18
Does this seahorse product manage both ssh and gnupg keys?? I think if you have an rsa key (I dont know if its a signing or encryption key -- but I don't think it would matter), its theoretically possible to use the same rsa key gnupg key for the ssh id_rsa key.  Again in order to apply this feature you would have to create the key with authenticate capabilities.  By default the signature key is made with sign (ability to sign documents) and certify (ability to sign other keys) capabilities.  If you added authenticate abilities to the key, I believe you could use the same key for ssh purposes (I believe since I've never done it but only read about it!)  Perhaps I should try this out!

---

### Post by seventhc on 2008-02-18
> Does this seahorse product manage both ssh and gnupg keys??Yes, if I open seahorse it shows me 2 keys, one I have for email and 1 for ssh. Each has their own key ID.
but gpg --list-keys only shows the one key for email

Edit: In all honesty the ssh key is there more for the purpose of understanding all of this. I use the main key for email and signing, have never used the ssh key. But want to learn how.

---

### Post by Herman on 2008-02-18
> In all honesty the ssh key is there more for the purpose of understanding all of this. I use the main key for email and signing, have never used the ssh key. But want to learn how. I'm here to learn too, I have only recently started getting interested in keys and encryption and this sort of thing since I was recently looking for ways to improve my [SSH Network]("http://users.bigpond.net.au/hermanzone/p11.htm") Page. I decided to try our Seahorse for the RSA key to add security to SSH and make it easier to use. Being able to encrypt files and email are also great security features.

What I've found out so far about how the SSH keys are used is this, Seahorse generates for us a pair of keys, a private and a public RSA key.
I'm not quite certain of all this information here but I'll have a try and it should be approximately correct.
As far as I know the only location these are saved is in the .ssh directory in a file called rd_rsa and a file called id_rsa.pub.
The file called rd_rsa contains our private key which we need to keep secret.
The file called id_rsa.pub contians our public key which is to be copied to our friend's computer, which we want to connect to.

To set up passwordless logins for SSH, we open Seahorse and right-click on our Private RSA key. Select 'Set up Computer for Secure Shell...'
A window opens titled 'Set up Computer for SSH Connection', and below that, there's a note: 'To use your Secure Shell key with another computer, you must already have a login account in that computer.

There's a field under that called 'Computer Name', meaning domain name I think, but I just type the IP number: port number (if other than 22), of the friend's computer there, that works for me.
There's also a field for your login name in the other computer, which is autocompleted.
When you are ready, click 'Setup'.
You'll be asked for the password to your account in your friend's computer, type it and click 'Okay'.
That's it! Your public RSA key is copied into your friend's computer, it's appended to a file called .ssh/authorized_keys.

Now when you open an SSH connection to your friend's computer, you may be asked for a keyring password for the first time connection, but after that the login should be automatic.
The way it works is something like this, the computer you are connecting to uses your public key to generate a number and encrypts the number and sets the encrypted number to your computer.
Your computer uses your private RSA key to decrypt the number and sends the unencrypted number back to your freind's computer. When your freind's computer receives the number back decrypted, that proves the identity of the computer you are using is genuine, since only your private key could have decrypted that number. The remote computer allows the connection and opens.
After the first time connection it's automatic, you don't need to type a password anymore.

Don't quote me on all this, I'm still reading, researching and experimenting myself, but I think that's somewhere close to a description of how to use Seahorse for RSA keys in SSH Networking.

Regards, Herman :)

---

### Post by seventhc on 2008-02-18
That was a good explanation on how the ssh key works, thanks :)
Makes more sense now.
Lots of info on your site too. :)

---

### Post by kevdog on 2008-02-18
It seems we have delved into the world of concepts rather than real problems which is a lot more interesting.

---

### Post by seventhc on 2008-02-18
But wouldn't that be a real world use?
Or you mean me having it when I don't ssh into another system? lol
Actually I did need it, hmm what was it for..launchpad or something I believe. not that I had to use it, but,.. I can't remember now, I'll have to look and find out why I needed it. I think they just wanted me to have one for some reason.

I will eventually set up a second computer just to test it out though. I also have a friend that lives about 2000 miles away and he sometimes sets up a server and we both ssh into it just to mess around, so next time I talk to him I'll see if we can do it this way for a better understanding of how it works.

---

### Post by Herman on 2008-02-21
Hello seventhc and kevdog,
:) I have just received some updates in Hardy Herron and all of a sudden Seahorse is showing my RSA keys for SSH now! :guitar:
I don't yet have an icon for 'Connect to Server' in my 'Places' menu, and port scanning doesn't show port 22 as being open yet, even though I have SSH server installed. Probably those problems will be fixed in some future update as well. I will just be patient. I can always boot into Gutsy Gibbon for whatever I need to do. I really like Hardy Herron, it will be the best Ubuntu yet by far when it is released in April. The Ubuntu developers are doing a great job.
Regards, Herman  :)

---

### Post by seventhc on 2008-02-21
So it is starting to get back to normal then?
Good. :):)
Maybe I'll try it again. :)
dual boot this time. :cool:

---

### Post by kevdog on 2008-02-21
I'll just wait -- feisty is good for me for the time being.

---

### Post by seventhc on 2008-02-21
I;m sticking with Gutsy for now too, but that can all change in a matter of  minutes. lol

---

