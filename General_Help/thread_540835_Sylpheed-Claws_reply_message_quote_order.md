---
title: "Sylpheed-Claws reply message quote order"
date: 2007-09-02
forum: General Help
---

### Post by charbo on 2007-09-02
Hi,

I started checking out Sylpheed-Claws, and I find it quite nice.

There is one thing I cannot figure out how to do, that bothers me a bit, though.

I usually like the quoted original message in reply messages to come underneath the reply message itself.   However, in Sylpheed Claws, the reply message is placed under the quote of original by default.  I went into  Configuration -> Preferences, and looked in Quoting, but I could not figure out how to change this.

Is it possible to change the order of quote of original message in Sylpheed Claws?
If so, how do you do that?

Please someone let me know. 
Thank you in advance.

Sadanori

---

### Post by moore.bryan on 2007-09-02
[I]absolutely... i find the default behavior less than desirable as well.  i did it by going into preferences, compose, templates and putting two empty lines in the top of the second box (the one which deals with reply quoting), putting the cursor back at the top, and applying the changes.  

let me know if that doesn't work for you...
[/I]

---

### Post by charbo on 2007-09-03
Thank you for your reply.

I am not sure if I am doing what you say, but it does not work for me.

In my copy, there is no template under compose in preferences.  So, I assumed, that it is, in my case, preferences->quoting under compose.  In the template text area I added two empty lines at the top, and put the cursor there at the top, and applied the change.

The result is that the two empty lines do show up, but the cursor stays at the bottom.

Am I not following you?
Any other thoughts?

Thank you very much again.
Sadanori

---

### Post by moore.bryan on 2007-09-03
*okay, that's a little strange because it worked for me.  try this... in your account preferences, there is a "templates" subdivision.  in there, the second box should deal with replies.  check the "use a specific reply quote format" and just leave it blank... does that do the trick?  if it does, you can just copy over the format to quote your reply; if not, we'll have to figure-out another fix.*

---

### Post by charbo on 2007-09-03
Thank you again for your response.

My account preferences, i.e. "Preferences for current account" does not have "templates" subdivision. nor I could find "use a specific reply quote format"check box anywhere under the Configuration menu.

My copy of Sylpheed-Claws is version 2.6.0.  Are we looking at the same thing?

Anyway, I really appreciate you trying to help me.  Thank you so much.
In case it might help, I am attaching a screen shot of the preferences window, which opens when I choose Preferences from Configuration menu.

---

### Post by moore.bryan on 2007-09-04
*alas, i'm running claws-mail 3.0.0... but, you should have some similar things.  try going to "configuration," "preferences for current account," and see if there's a "quoting" choice in the left menu.  if so, change that to mirror the general preferences as above.*

---

### Post by charbo on 2007-09-05
Thank you for your reply again.

hmmm, that is basically what I am trying to do.
I mean, in Configuration, under Preferences, I choose the quoting from the left pane, and in the second box, I give two additional lines at the top, and place the cursor at the top, when I press apply.  Still, the cursor stays at the bottom, when I actually reply to messages, and I have to click in the message once before I start typing the message, which is a little annoyance. 

Oh, well, I guess I will wait until the version in the repo is upgraded to 3.0.  At least it is nice to know that in the near future, it will be fixed to my liking.

Thank you again, for all your support until now.

Sadanori

---

### Post by colinleroy on 2007-09-05
> **charbo said:**
> Hi,

I started checking out Sylpheed-Claws, and I find it quite nice.

There is one thing I cannot figure out how to do, that bothers me a bit, though.

I usually like the quoted original message in reply messages to come underneath the reply message itself.   However, in Sylpheed Claws, the reply message is placed under the quote of original by default.  I went into  Configuration -> Preferences, and looked in Quoting, but I could not figure out how to change this.

Is it possible to change the order of quote of original message in Sylpheed Claws?
If so, how do you do that?

Please someone let me know. 
Thank you in advance.

Sadanori

You can use a template like:

--------------
%X 

Your name

%q
--------------

%X is the cursor's place, %q the quoted original message. 

Although, top-posting isn't logical :)

---

### Post by charbo on 2007-09-08
Thank you so much.
This worked!!

What do you mean by top-posting?
You mean that the most recent reply on top and the history of messages at the bottom?

If so, I can understand that some people think it is not logical.
My take on it is that the history of messages is an optional reference to the reply message, and as such, for me it makes sense to have the reply at the top.:)

Thank you again for the help!

---

