---
title: "General Questions AWS EC2 Instances S3"
date: 2016-08-02
forum: General Help
---

### Post by kenneth20 on 2016-08-02
Hi, 

I am a beginner and I am trying to launch a dynamic website, hopefully by the end of this year. 

So Far I have created all the structure of the website, but I just have it as a statice website hosted in S3 by AWS. 

I was trying to launch an Instance, but, I need to learn a few things:

-When I launch my instance an I am able to connect to it, what should I do if I install LAMP?, should I log into myphp on browser or can I do everything in CLI?
-the documnetation talks about terminating the instance at some point: see the following: the question is, shuold I terminate the instance, and why would I do it? shouldn't I just leave the instance run 24/7 as my website shuold stay live?


[https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EC2_GetStarted.html#ec2-connect-to-instance-linux](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EC2_GetStarted.html#ec2-connect-to-instance-linux)
To terminate your instance

[LIST]
[*]In the navigation pane, choose Instances. In the list of instances, select the instance.

[*]Choose Actions, then Instance State, and then choose Terminate.

[*]Choose Yes, Terminate when prompted for confirmation.
Amazon EC2 shuts down and terminates your instance. After your instance is terminated, it remains visible on the console for a short while, and then the entry is deleted.
[/LIST]
If there was a good tutorial about php that I could take if some one knows I would appreciate it.

---

### Post by Habitual on 2016-08-02
Most of the work I do in AWS is command-line driven.
I am certain there are Images out there that have LAMP stacks fully implemented.
It's been my experience, that it's best I install them.
I leave my instances running.

I never use Terminate as **it destroys the instance** with no chance of recovery, of anything.
Unless of course, I mean to destroy it.

Have a look at [Getting Started with AWS]("https://aws.amazon.com/documentation/gettingstarted/") and specifically [Hosting a Static Website on Amazon Web Services]("http://docs.aws.amazon.com/gettingstarted/latest/swh/website-hosting-intro.html")

Have fun.

---

### Post by kenneth20 on 2016-08-03
Have you been able to configure an e-mail client for AWS workMail?

---

### Post by Habitual on 2016-08-03
> **kenneth20 said:**
> Have you been able to configure an e-mail client for AWS workMail?

See [Getting Started With Amazon WorkMail]("http://docs.aws.amazon.com/workmail/latest/userguide/getting_started.html")

---

