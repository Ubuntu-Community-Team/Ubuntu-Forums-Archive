---
title: "Can't access to Ubuntu One when i try to write a review"
date: 2015-02-23
forum: General Help
---

### Post by enricobe on 2015-02-23
Hello,
my Ubuntu is in Italian so the error message could be different from what i write here, but the problem is very simple.

When I open the Ubuntu Software Center and i try to write a review for a program I get the "Can't access" error. In italian is "Accesso non riuscito": the Login to Ubuntu One fails. How can i fix this problem? 
[ATTACH=CONFIG]260170[/ATTACH]

---

### Post by jim_deadlock on 2015-02-23
You can't. Ubuntu One was shut down a few months ago.

---

### Post by enricobe on 2015-02-23
So there is no way to write reviews? All the reviews in the software center are old?

---

### Post by coffeecat on 2015-02-23
> **enricobe said:**
> So there is no way to write reviews? All the reviews in the software center are old? 

jim_deadlock was referring to the Ubuntu One cloud service which was closed down last year, and which has nothing to do with Ubuntu One single sign on, which is what you need to write a review in the Software Centre. Clearly, your Ubuntu One SSO account is working since you have been able to log into the forum. There is the occasional thread about your problem, but I'm sorry I can't remember if there was any answer to get round this. I have just successfully logged in to the Software Centre review section via Ubuntu One, so that means that others can too and there must be recent reviews.

Sorry that I have no answer for you, but perhaps someone else might. If anyone else refers to Ubuntu One being closed, they are talking about Ubuntu One cloud services, which is not relevant.

---

### Post by coldraven on 2015-02-23
It should work. Calling it "Ubuntu One" is a bit misleading because as jim_deadlock says it was shut down.
I just tried to write a review and got these pop-up windows.
The second one appears when I clicked "Login with my existing account"

---

### Post by coffeecat on 2015-02-23
> **coldraven said:**
> Calling it "Ubuntu One" is a bit misleading because as jim_deadlock says it was shut down.


It is not at all misleading. Ubuntu One Single Sign On is called Ubuntu One Single Sign On. Even your second screenshot says "Ubuntu One". As does this:

[https://login.ubuntu.com/](https://login.ubuntu.com/)

Granted it was confusing for Canonical to refer to their now-defunct cloud services as Ubuntu One as well, but it merely confuses the OP to say that Ubuntu One has been shut down when the closed Ubuntu One cloud service has absolutely nothing to do with signing in to Software Centre.

---

### Post by enricobe on 2015-02-23
> **coffeecat said:**
> jim_deadlock was referring to the Ubuntu One cloud service which was closed down last year, and which has nothing to do with Ubuntu One single sign on, which is what you need to write a review in the Software Centre. Clearly, your Ubuntu One SSO account is working since you have been able to log into the forum. There is the occasional thread about your problem, but I'm sorry I can't remember if there was any answer to get round this. I have just successfully logged in to the Software Centre review section via Ubuntu One, so that means that others can too and there must be recent reviews.

Sorry that I have no answer for you, but perhaps someone else might. If anyone else refers to Ubuntu One being closed, they are talking about Ubuntu One cloud services, which is not relevant.

Thank you for your explanation. 

I did the login with the Ubuntu One SSO in the Ubuntu Software Center, and worked for one or two days. But now i can't access.

Could I try to remove the Ubuntu Software Center with ap-get remove? Could it fix the problem?

---

### Post by coffeecat on 2015-02-23
> **enricobe said:**
> Could I try to remove the Ubuntu Software Center with ap-get remove? Could it fix the problem?

I wouldn't advise that, but I do have one suggestion. Since you are already logged into Software Centre, you will remain logged in indefinitely, unless you do the following.

Open the dash and search for Passwords and Keys. In Passwords and Keys, under Passwords/Login, highlight the Ubuntu One line, right click and delete. That will log you out of Ubuntu Software Centre properly. Now try to write your review again, and you should be presented with the screens that coldraven posted - click on Log-in with my existing account in the first screen. Log into Software Centre by logging into Ubuntu One using the same Ubuntu One email address and password that you use for this forum account (assuming you use the same Ubuntu One account for everything), and hopefully whatever was causing the problem will be by-passed.

---

### Post by enricobe on 2015-02-23
> **coffeecat said:**
> I wouldn't advise that, but I do have one suggestion. Since you are already logged into Software Centre, you will remain logged in indefinitely, unless you do the following.

Open the dash and search for Passwords and Keys. In Passwords and Keys, under Passwords/Login, highlight the Ubuntu One line, right click and delete. That will log you out of Ubuntu Software Centre properly. Now try to write your review again, and you should be presented with the screens that coldraven posted - click on Log-in with my existing account in the first screen. Log into Software Centre by logging into Ubuntu One using the same Ubuntu One email address and password that you use for this forum account (assuming you use the same Ubuntu One account for everything), and hopefully whatever was causing the problem will be by-passed.

THANKS! It worked! :D

---

### Post by deadflowr on 2015-02-23
Well, since you've seemed to have solved the issue, you can [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") if you like.

Also, out of curiosity, what program did you review, if I may ask?

---

### Post by enricobe on 2015-02-23
> **deadflowr said:**
> Well, since you've seemed to have solved the issue, you can [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") if you like.

Also, out of curiosity, what program did you review, if I may ask?

I reviewed Audacity, but also want to review others programs like OpenShot, 0 A.D., Edgewars, etc. I think the reviews are really useful to have some information before the install of the program. There are only few reviews in the Italian version of Software Center

---

