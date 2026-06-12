---
title: "Password Length"
date: 2007-05-12
forum: General Help
---

### Post by sthompson on 2007-05-12
I'm using Feisty Fawn. What is the maximum password length for user logins?

Thanx,

Steve

---

### Post by Martje_001 on 2007-05-13
There are no limitations.. (correct me if I'm wrong..)

---

### Post by Cheese Sandwich on 2007-06-29
> **Martje_001 said:**
> There are no limitations.. (correct me if I'm wrong..)

I've run into a silent maximum length of 8:

[http://ubuntuforums.org/showthread.php?t=488046](http://ubuntuforums.org/showthread.php?t=488046)

---

### Post by stchman on 2007-06-29
> **Cheese Sandwich said:**
> I've run into a silent maximum length of 8:

[http://ubuntuforums.org/showthread.php?t=488046](http://ubuntuforums.org/showthread.php?t=488046)

I will have to give that a try.

I will make an account and give it a 15 character password and only type in the first 8.  I will post the findings here.

My password for my account is also 8 characters as well.  I wonder what the strength of a 8 character password is?

I gather that with all symbols, number, latters (lower and uppercase) that 8 characters is pretty strong.

---

### Post by Cheese Sandwich on 2007-06-29
> **stchman said:**
> I will have to give that a try.

I will make an account and give it a 15 character password and only type in the first 8.  I will post the findings here.

My password for my account is also 8 characters as well.  I wonder what the strength of a 8 character password is?

I gather that with all symbols, number, latters (lower and uppercase) that 8 characters is pretty strong.

Please see the updated thread, I had set the password through webmin. When I set it via "passwd", that implements it correctly.

Could be a webmin thing. What I found strange is that logins to console or SSH accepted the extra characters without complaint.

---

### Post by Cheese Sandwich on 2007-06-29
Confirmed it's a webmin thing.

---

### Post by kevinlyfellow on 2007-06-29
> **stchman said:**
> 
My password for my account is also 8 characters as well.  I wonder what the strength of a 8 character password is?

I gather that with all symbols, number, latters (lower and uppercase) that 8 characters is pretty strong.

I think there are about 75 usable characters and if we assume the password is (inclusive) between 6 to 8 characters, there are about 10^15 different possibilities (actually even if 8 is required, the approximation is still the same).  Safe if it's random.  To put that into perspective, if a hacker could make 10 attempts a second, it would take 3 million years to go through every possibility.

---

### Post by Cheese Sandwich on 2007-06-29
> **kevinlyfellow said:**
> I think there are about 75 usable characters and if we assume the password is (inclusive) between 6 to 8 characters, there are about 10^15 different possibilities (actually even if 8 is required, the approximation is still the same).  Safe if it's random.  To put that into perspective, if a hacker could make 10 attempts a second, it would take 3 million years to go through every possibility.

Agreed, however you could reduce that number by taking into account, for example, the biases of English-speaking humans when attempting to choose a "random" password, for example. Also, many people will not consider using characters such as upper-case letters or symbols such as $%^@&, etc.

---

### Post by kevinlyfellow on 2007-06-29
> **Cheese Sandwich said:**
> Agreed, however you could reduce that number by taking into account, for example, the biases of English-speaking humans when attempting to choose a "random" password, for example. Also, many people will not consider using characters such as upper-case letters or symbols such as $%^@&, etc.

Yeah, it is hard to get people to use random passwords... I guess I'm in the paranoid minority (I use a randomly generated password, with uppercase, lowercase and characters).  I started using one when someone tried to crack into my ssh server.  

with only lowercase and numbers, the possibilities drop to about 10^12.  Still the difficult part is getting people not to use common words!

---

### Post by Cheese Sandwich on 2007-06-29
> **kevinlyfellow said:**
> Yeah, it is hard to get people to use random passwords... I guess I'm in the paranoid minority (I use a randomly generated password, with uppercase, lowercase and characters).  I started using one when someone tried to crack into my ssh server.  

with only lowercase and numbers, the possibilities drop to about 10^12.  Still the difficult part is getting people not to use common words!

You can carry it even further, by taking into account the fact that english speakers tend to favor certain letter over others, and would probably insert numbers at the very beginning or end (except perhaps for the number 2, to replace the words "to" or "too").

---

### Post by euler_fan on 2007-06-29
It is very disappointing to hear that there is a problem in the Feisty password system. Has a bug report been filed?

I don't use random passwords, but i do try to exploit the number game a bit.

I tend to prefer passwords at least 12-14 characters long with uppercase, lowercase, numbers, and symbols in them. For really sensitive things I have gone over 20. But the size of the base character set is not as important as length. It is completely possible to create a secure password with just lowercase letters--the problem is it would need to be several characters longer.

Example:

an 8 character password randomly drawn from uppercase and lowercase letters has 52^8=5.35x10^13 passwords. However, a password randomly drawn from only 26 characters need only be 10 characters long to  have 2.6 times as many possible passwords to chose from.

Further, increasing the base alphabet to 75 letters as another poster suggests does not even reduce the required length to have at least as many passwords as the "8 from 52 with repetitions" case. It turns out, however, that 75^8=1x10^15, a mere 18 times as many possible passwords as opposed to 52 times by merely making the 8 character password from a 52 letter alphabet a nine letter password.

Ergo, I go for longer before I go for more of anything else as a general rule.

@Everyone: is trying 10 passwords/second realistic? I was under the impression with modern computers and connections hundreds or even thousands of passwords can be ran per second.

---

### Post by Cheese Sandwich on 2007-06-29
> **euler_fan said:**
> It is very disappointing to hear that there is a problem in the Feisty password system. Has a bug report been filed?


I filed a bug at webmin regarding the issue, not sure if it's actually an ubuntu bug (or even a bug at all, instead of a missing feature, so to speak).

---

### Post by euler_fan on 2007-06-29
> **Cheese Sandwich said:**
> I filed a bug at webmin regarding the issue, not sure if it's actually an ubuntu bug (or even a bug at all, instead of a missing feature, so to speak).

Thanks. "missing features" in basic security items worry me a bit. :-|

---

### Post by Herman on 2007-06-29
Maybe it's only in some installations, I have a sixteen character password for my Ubuntu Feisty AMD64 install from the 'Alternate CD', and I can't log into that without all sixteen characters being correct. I couldn't use 'sudo' either. :D
I'll test a few other Ubuntu installs, but I don't have Xubuntu at the moment, did you say it was Xubuntu that you're noticing this in?

Any comments on my revised [password tip]("http://users.bigpond.net.au/hermanzone/p2.htm#password_tip") here in the 'Alternate CD' install in 'Illustrated Dual Boot' site? By a co-incidence I just improved that this morning before seeing this thread. I think I have worked out a good way for people to be able to have a good secure password that they'll easily be able to remember, (so they don't have to have it written down anywhere someone else could find it). I used to show how to make just an eight character password before I editied it this morning.
What do you think?

Edit: I was unable to log into my wife's computer via SSH on our LAN without all the characters in her password. She's running Feisty Fawn and Dapper Ultimate Edition.

---

### Post by Cheese Sandwich on 2007-06-29
> **Herman said:**
> 
Edit: I was unable to log into my wife's computer via SSH on our LAN without all the characters in her password. She's running Feisty Fawn and Dapper Ultimate Edition.

This problem only occurs for me when I set the password via webmin.

---

### Post by kevinlyfellow on 2007-06-30
> **euler_fan said:**
> It is very disappointing to hear that there is a problem in the Feisty password system. Has a bug report been filed?

I don't use random passwords, but i do try to exploit the number game a bit.


I honestly don't see this as a bug!  If you choose a randomly generated password, it is almost unbreakable.  If you choose a password (randomly generated) with only lowercase and numbers, it's still very strong.  There really is only a big issue when someone uses words that can be found in a cracker's dictionary.  If that is the case, it does not matter whether your password is 8 characters or 12, you can be cracked!

> 
@Everyone: is trying 10 passwords/second realistic? I was under the impression with modern computers and connections hundreds or even thousands of passwords can be ran per second.

By default there is a pause between login events.  Ssh can be configured (and should be by default if it isn't) to only allow a single ip to have a login attempt every x number of seconds.  I know when a cracker tried to get into my computer, this didn't seem to be the case, but if I remember correctly, they attempted about 90 logins within a few minutes.  But, lets say 1000 attempts could be made every second and you chose from only lowercase characters and numbers.  That's still about 30 years that it would take to go through every possibility.  Suppose the cracker would waste 24 hour on your machine (if a cracker wastes more than that, then you must have something they really want... in which case you better learn how to setup ssh to block multiple failed login attempts).  That means the cracker has gone through 0.000088 (8.8*10^-5) of the possible passwords (sorry I'm too lazy to calculate the probabilities and I'm sure the number is slightly off since I've mostly been doing order of magnitude calculations).  I put tons of advantages to the cracker, but still if very unlikely that the login attempt was successful.  In the end, the best way to avoid being cracked is to stay out of the dictionaries.  Also another thing to keep in mind is that they will also try to guess your username, which could be difficult enough in itself since an ssh rejection does not differentiate between having a wrong username and a wrong password. 

If you want to check to see how secure your password is, you can use any of the tools out there to do so.  Unless you really have something that someone wants, no one is going to spend the time to break into your system via guessing a password.  The biggest targets are people with easy to guess passwords.

---

### Post by euler_fan on 2007-06-30
> **kevinlyfellow said:**
> I honestly don't see this as a bug!  If you choose a randomly generated password, it is almost unbreakable.  If you choose a password (randomly generated) with only lowercase and numbers, it's still very strong.  There really is only a big issue when someone uses words that can be found in a cracker's dictionary.  If that is the case, it does not matter whether your password is 8 characters or 12, you can be cracked!



By default there is a pause between login events.  Ssh can be configured (and should be by default if it isn't) to only allow a single ip to have a login attempt every x number of seconds.  I know when a cracker tried to get into my computer, this didn't seem to be the case, but if I remember correctly, they attempted about 90 logins within a few minutes.  But, lets say 1000 attempts could be made every second and you chose from only lowercase characters and numbers.  That's still about 30 years that it would take to go through every possibility.  Suppose the cracker would waste 24 hour on your machine (if a cracker wastes more than that, then you must have something they really want... in which case you better learn how to setup ssh to block multiple failed login attempts).  That means the cracker has gone through 0.000088 (8.8*10^-5) of the possible passwords (sorry I'm too lazy to calculate the probabilities and I'm sure the number is slightly off since I've mostly been doing order of magnitude calculations).  I put tons of advantages to the cracker, but still if very unlikely that the login attempt was successful.  In the end, the best way to avoid being cracked is to stay out of the dictionaries.  Also another thing to keep in mind is that they will also try to guess your username, which could be difficult enough in itself since an ssh rejection does not differentiate between having a wrong username and a wrong password. 

If you want to check to see how secure your password is, you can use any of the tools out there to do so.  Unless you really have something that someone wants, no one is going to spend the time to break into your system via guessing a password.  The biggest targets are people with easy to guess passwords.

Thanks for that. I guess I might just be paranoid, but like I said, I'm not using random passwords :)

But even with random passwords, the expected number of passwords to be tried is 1/2 the total number possible (assuming that the password is drawn uniformly and randomly). The variance is 1/12 the number of passwords avaliable. Doubling the number of possible passwords doubles those times till they expect to have guessed. And often they will guess much faster, given the variance (one standard deviation here is about 1/(3.4)). And that's assuming a fixed password length, which is issue here. Having multiple lengths is properly implemented password system will but further decrease the odds of a successful guess. But as you say, too few of use use random passwords even of length 8. Imagine how many fewer bots there would be on the web if strong passwords were enforced as a default on all systems :rolleyes:

But it's also as you point out about level of risk. The world's DNS servers doubtless under much more risk than you or I am.

Nonetheless, until I switch to truly random passwords, I'll stick with making mine ridiculously long.

---

### Post by kevinlyfellow on 2007-06-30
> **euler_fan said:**
> Thanks for that. I guess I might just be paranoid, but like I said, I'm not using random passwords :)

But even with random passwords, the expected number of passwords to be tried is 1/2 the total number possible (assuming that the password is drawn uniformly and randomly). The variance is 1/12 the number of passwords avaliable. Doubling the number of possible passwords doubles those times till they expect to have guessed. And often they will guess much faster, given the variance (one standard deviation here is about 1/(3.4)). And that's assuming a fixed password length, which is issue here. Having multiple lengths is properly implemented password system will but further decrease the odds of a successful guess. But as you say, too few of use use random passwords even of length 8. Imagine how many fewer bots there would be on the web if strong passwords were enforced as a default on all systems :rolleyes:

But it's also as you point out about level of risk. The world's DNS servers doubtless under much more risk than you or I am.

Nonetheless, until I switch to truly random passwords, I'll stick with making mine ridiculously long.

Using common words is a dangerous practice.  You can decrease your odds with a longer password, but I'm not sure that double the password length will double the amount of time it takes to break in (random or not.  I'll take a look at this when I have some time.).  A great strategy to use is coming up with pseudo random passwords that are still easy for you remember.  For instance, I can open up my favorite book and take the first letter of each chapter title for the first 8 chapters.  I throw in my favorite chapter's number in there somewhere, change the capitalization of a few chapters that were notable and BAM!  I've got a great password.  

But I agree that there should be no limit of password length (I put up a fight because I getting the feeling that a consensus may have been made that 8 would be unsafe, when that's not true).  There is no good reason to limit a password's security, and if a user wants a password thats 6 or 20 characters long, that user should be allowed to.

---

### Post by euler_fan on 2007-06-30
> **kevinlyfellow said:**
> Using common words is a dangerous practice.  You can decrease your odds with a longer password, but I'm not sure that double the password length will double the amount of time it takes to break in (random or not.  I'll take a look at this when I have some time.).  A great strategy to use is coming up with pseudo random passwords that are still easy for you remember.  For instance, I can open up my favorite book and take the first letter of each chapter title for the first 8 chapters.  I throw in my favorite chapter's number in there somewhere, change the capitalization of a few chapters that were notable and BAM!  I've got a great password.  

But I agree that there should be no limit of password length (I put up a fight because I getting the feeling that a consensus may have been made that 8 would be unsafe, when that's not true).  There is no good reason to limit a password's security, and if a user wants a password thats 6 or 20 characters long, that user should be allowed to.

On the time part, I assumed that a random password is drawn uniformly from all possible passwords constructible from a given length alphabet in lexicographical order, and used the expected value formula for a uniform random variable to find out how many guesses would be needed on average to find the correct one. If you double the number of passwords you double the expected number needed to randomly find the correct one and thus, at a fixed number of tries per time, double the time. It should all be in the Wikipedia site about "uniform distribution" or "uniform random variable".

I agree completely about not using common words. They are an absolutely bad idea in passwords. I didn't mean to imply I use dictionary words or simple l33tings thereof, which really aren't much better as my other math demonstrated (even under ideal circumstances). Ergo, I have my own algorithm for generating long memorable passwords that hopefully look nothing like something out of the dictionary, l33t3d or not :) As time goes on I think I'll probably start using KeePassX or another such utility to generate truly random ones and switch over.

I have a friend who used to use the same 6 character password for everything and helped her set up unique random passwords for everything. After watching her completely memorize them in a few weeks I've realized it really isn't as hard as I once thought to memorize completely random strings.

---

