---
title: "Make Ubuntu automatically log people out"
date: 2019-04-05
forum: General Help
---

### Post by heroquestelf on 2019-04-05
Hey folks, I have a question, and I’m not sure if I’m asking for an app recommendation or a script publication… I have kind of a weird setup and I’m looking for a solution.
 
 
 First off, I have a computer at my workplace that is running **Ubuntu MATE 18.01.2**. It has about 5-8 individual users and each of these individual users has their own login to the machine. I am the only person with root access and, in fact, I have most of the control over the machine because when we give out accounts to the machine we don’t give out passwords. Basically, whenever anyone wants to use the machine they have to ask permission so that I can log them in.

 
 
 The main reason for all of this control is that this is the machine that people use when they’re on break. This is the “goof off, play video games and watch YouTube” machine. Very rarely do I have someone using the computer to do anything that I would describe as “productive”. This machine is essentially a  big toy.  
 
 
 Now, that all being said, if you’re using this machine you have a limit of 20 minutes. Now, given all the other PC nonsense that I have to deal with I don’t always have time to enforce this limit. So I’m looking to see if I can’t automate the process.  
 
 
 I know how to do Timeout commands. I’ve seen the “shutdown +20” commands, so I know I have script options, but I would like two elements of flexibility.  
 
 
 #1. I’d like something that could warn people when they have 5 minutes left.
 #2. There are times when I’d like to be able to extend people’s time limit to 30 minutes.  

 
 
 So that leaves me with two questions:
 
 
 #1. Is there an inexpensive and/or open source application that would do this?
 **OR**

 #2. Is there a script I could use to achieve this same goal. (Keeping in mind that when anyone uses the machine I have to be the one to log them in so it wouldn’t be difficult to open a terminal and execute a script real quick before I walk away from the machine—also, it bears mentioning that I’m the only person with any Linux literacy, so it’s not like anyone could disable a running script.)

---

### Post by #&amp;thj^% on 2019-04-05
What about "pkill"
```
pkill -KILL -u {username}
```
Example:
User name "me" as a plain user:
```
# pkill -KILL -u me
```
[B]Beware: Do not kill root user or other system level user process. The following example, will kill all process on your server Or Desktop. Do not run the pkill for root user:
"pkill -KILL -u root"[/B]

To see list of logged in user type who or w command:
```
# who
```

OR
```

# w
```
As for a warning of expiration time left, I just don't know.

---

### Post by again? on 2019-04-05
There is an application called timekpr installable from a ppa.
It's an old application that someone revamped to work with Ubuntu.
Fairly simple to use.

Set the time period from the second tab (Limits & Boundaries) and hit "Apply".
[ATTACH=CONFIG]282972[/ATTACH]

Use the first tab (Status) to clear all restrictions, reset time period or add extra time.
[ATTACH=CONFIG]282973[/ATTACH]

I tested in Xubuntu 18.04 and all seemed to work ok.
Shows time left notifications and when limit is reached waits a couple of minutes before logging out,
It's supposed to work in Mate but you will need to test.

[B][COLOR="#FF0000"]**Make sure you have a user account with admin privileges other than the one your restricting access to,
so you can easily rectify if problems occur.**[/COLOR][/B]

To install...
```
sudo add-apt-repository ppa:mjasnik/ppa
sudo apt install timekpr
```
May need to log out for the panel indicator to work.

The developer has plans to release a completely new version... [https://launchpad.net/timekpr-next/+announcement/15243](https://launchpad.net/timekpr-next/+announcement/15243)

---

### Post by #&amp;thj^% on 2019-04-06
> **guber2 said:**
> There is an application called timekpr installable from a ppa.
It's an old application that someone revamped to work with Ubuntu.
Fairly simple to use.

Set the time period from the second tab (Limits & Boundaries) and hit "Apply".
[ATTACH=CONFIG]282972[/ATTACH]

Use the first tab (Status) to clear all restrictions, reset time period or add extra time.
[ATTACH=CONFIG]282973[/ATTACH]

I tested in Xubuntu 18.04 and all seemed to work ok.
Shows time left notifications and when limit is reached waits a couple of minutes before logging out,
It's supposed to work in Mate but you will need to test.

[B][COLOR="#FF0000"]**Make sure you have a user account with admin privileges other than the one your restricting access to,
so you can easily rectify if problems occur.**[/COLOR][/B]

To install...
```
sudo add-apt-repository ppa:mjasnik/ppa
sudo apt install timekpr
```
May need to log out for the panel indicator to work.

The developer has plans to release a completely new version... [https://launchpad.net/timekpr-next/+announcement/15243](https://launchpad.net/timekpr-next/+announcement/15243)

Nice find guber2,:KS just to confirm it works well with Mate, you'll find it after you install and logout under>>System>>Administration

---

### Post by mjasnik on 2019-04-26
Hi!

Please use timekpr-next for this, it's released as beta now, but works fine on my sons machine for 4-5 months already :)
It has many new advancements over old timekpr and has no permanent account locking, please read more [https://launchpad.net/timekpr-next](https://launchpad.net/timekpr-next) or in my announcement [https://launchpad.net/timekpr-next/+announcement/15249](https://launchpad.net/timekpr-next/+announcement/15249) .

It's in the same PPA as revived, all You need to do is: sudo apt-get install timekpr-next-beta
If You have questions or find problems, please report them to me via launchpad.
Hope You find this useful :)

regards
Eduardo

---

### Post by again? on 2019-04-26
Thank you very much Eduardo, for sharing your work.
Although I have no need to use myself, those with school age children will find it an essential tool.

---

