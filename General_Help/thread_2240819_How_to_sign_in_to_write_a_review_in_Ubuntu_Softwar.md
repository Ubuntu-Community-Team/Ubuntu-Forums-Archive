---
title: "How to sign in to write a review in Ubuntu Software Centre"
date: 2014-08-22
forum: General Help
---

### Post by Nosphky on 2014-08-22
In 14.04, I thought I would write a few words of review for an application in the Software Centre.  Having clicked on 'write your own review'  I get another window pop up with a spinning wheel which says 'Signing in'.

The wheel stays spinning for ever.  The only other option available in this window is the cancel button.  I've tried many times without any progress.

Where is it trying to sign me in to ?  Is there another way of getting there ?

---

### Post by slickymaster on 2014-08-22
Select ***"More information about the application"*** in the software center and a write review hot link appears. Clicking the link the user can create a software center account when the dialog box appears. I don't know if account activation is immediate though.

---

### Post by Nosphky on 2014-08-22
Hi slickymaster, that's the route I took.  All I get is the pop up window with the signing in message.  I've left it spinning for up to an hour on occasions.  It never seems to get 'there' where-ever 'there' might be.

---

### Post by slickymaster on 2014-08-22
> **Nosphky said:**
> Hi slickymaster, that's the route I took.  All I get is the pop up window with the signing in message.  I've left it spinning for up to an hour on occasions.  It never seems to get 'there' where-ever 'there' might be.

yeah, I've just checked and the same is happening here. It just hanging in "Signing in..." window :p

---

### Post by Nosphky on 2014-08-28
It's five days now and nothing's changed.  Is the system of writing reviews for software packages broken or dis-continued ? Where would be the best place to check ?

---

### Post by coffeecat on 2014-08-28
I don't know why you are getting a perpetually spinning wheel, but for me the "signing in" message resolves within a few seconds to a window inviting me to create an Ubuntu One account or to log in with my pre-existing Ubuntu One account. Logging in to my Ubuntu One account takes me to a window with fields for me to write my review.

---

### Post by slickymaster on 2014-08-28
> **coffeecat said:**
> I don't know why you are getting a perpetually spinning wheel, but for me the "signing in" message resolves within a few seconds to a window inviting me to create an Ubuntu One account or to log in with my pre-existing Ubuntu One account. Logging in to my Ubuntu One account takes me to a window with fields for me to write my review.

I'm still, also, facing the same issue the OP has. After clicking the "Write your own review" I get stuck hanging in "Signing in..." window. :mad:

---

### Post by coffeecat on 2014-08-28
> **slickymaster said:**
> I'm still, also, facing the same issue the OP has. After clicking the "Write your own review" I get stuck hanging in "Signing in..." window. :mad:

What is curious is that now that I have signed in once, Software Centre takes me straight to the review window, remembering who I am, even after closing SC or after a reboot. So there's probably a configuration file somewhere that has details of my logged in state, but I cannot find it. As this might provide a clue as to why you and the OP get stuck at the "signing in" window, it light be worth finding. Do you have any ideas where it might be?

---

### Post by Nosphky on 2014-08-28
Coffeecat : The only time I get invited to log in using Ubuntu One is on these forums.  Your remark about a config file has made me look and I find ~/.config/software-center.

This is very sparse but on my machine it is :
[general]
size = 1200, 970
maximized = False
recommender_uuid = 
recommender_opt_in_requested = False
add_to_launcher = True

[reviews]
username = 

So it looks like it never got initialised.  Maybe it needs me to login first ?  Spinning wheel comes to mind.

---

### Post by slickymaster on 2014-08-28
There's this config file [B]~/.config/software-center/softwarecenter.cfg
[/B]
Mine looks like this:```
[general]
size = 1088, 800
maximized = True
recommender_uuid =
recommender_opt_in_requested = False
add_to_launcher = True

[reviews]
username = 

```
Not sure if it's related, or not, but the 'username' parameter for mine is blank.

---

### Post by slickymaster on 2014-08-28
> **Nosphky said:**
> Coffeecat : The only time I get invited to log in using Ubuntu One is on these forums.  Your remark about a config file has made me look and I find ~/.config/software-center.

This is very sparse but on my machine it is :
[general]
size = 1200, 970
maximized = False
recommender_uuid = 
recommender_opt_in_requested = False
add_to_launcher = True

[reviews]
username = 

So it looks like it never got initialised.  Maybe it needs me to login first ?  Spinning wheel comes to mind.

I don't think that's related. I edit my ~/.config/software-center/softwarecenter.cfg file, adding my Ubuntu One account username to it, to no avail. Still the issue subsists.

What puzzles me is that applications's global (i.e., systemwide) configuration files are stored in **/etc**, but as far as I know the software center does not use any such configuration files.

---

### Post by coffeecat on 2014-08-28
> **Nosphky said:**
> Coffeecat : The only time I get invited to log in using Ubuntu One is on these forums.  Your remark about a config file has made me look and I find ~/.config/software-center.

This is very sparse but on my machine it is :
[general]
size = 1200, 970
maximized = False
recommender_uuid = 
recommender_opt_in_requested = False
add_to_launcher = True

[reviews]
username = 

So it looks like it never got initialised.  Maybe it needs me to login first ?  Spinning wheel comes to mind.

My ~/.config/software-center/softwarecenter.cfg is nearly the same:

```
[general]
size = 1200, 800
maximized = False
add_to_launcher = True
recommender_uuid = 
recommender_opt_in_requested = False

[reviews]
username = 

```

That's with my logged in state remembered. I tried deleting it but without effect and it was simply regenerated when I closed Software Centre. I haven't tried actually adding any reviews, which is probably why the bit after [reviews] is as it is. The Ubuntu One login details for Software Centre must be elsewhere.

---

### Post by Nosphky on 2014-08-28
I'm afraid it's broken.  I've been to launchpad.net and there's a bunch of bugs reported.  The latest seems to be :

[Bug #1316481]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1316481")    of 6 may 2014.

---

### Post by slickymaster on 2014-08-29
Thanks for finding out that bug report Nosphky. Going to add myself to it as it's also affecting me.

---

### Post by Entheo on 2014-12-21
Just to confirm that the same happens to me. I see recent reviews on USC though so some people are managing ok. I wonder if this will be resolved anytime soon?

---

### Post by Simon_Reed on 2015-04-04
I have never managed to get the reviewing to work since I started using Ubuntu at 10.04.  Many times I have wanted to write reviews, never been able to.

I am currently staring at the spinning wheel on a "Signing in..." screen on a Xubuntu 14.04 system.  The workaround to run "passwords and keys" won't work as I'm not aware of any such function in Xubuntu.

---

