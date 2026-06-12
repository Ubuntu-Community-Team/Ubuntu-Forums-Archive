---
title: "Lowercase &quot;s&quot; key doesn't work ..."
date: 2008-05-17
forum: General Help
---

### Post by gstuart on 2008-05-17
Hello - All of a sudden my lowercase "s" key doesn't work when composing messages using Sylpheed-Claws (v.2.6.0, on Ubuntu 6.06 LTS). Every time I type a lowercase "s", it "undoes" / deletes text, recursively each time the "s" key is pressed.  It's only the lowercase "s" key, as far as I know.

I did some Ubuntu system updates today (6.06 LTS, via the update manager) - this may be related, though I can't see why ...

Any ideas?

---

### Post by gstuart on 2008-05-18
FYI: I updated (directly) from Ubuntu 6.06 LTS to 8.04 LTS - this did not help ...

---

### Post by gstuart on 2008-05-18
Hello - For posterity, I found the solution, as described here.  Somehow, I had accidently set up "S" as the Undo hotkey ...

 ========================================

From: Greg
To: claws-mail-users@***
Subject: Re: Help - lowercase "s" key now deletes text in Sylpheed mail composer
Date: Sun, 18 May 2008 09:58:33 -0400

Hi Paul: Thank you for your reply ... I upgraded Ubuntu last evening (directly) from 6.06 LTS to 8.04 LTS, which also upgraded Claws Mail from version 2.6.0 (Sylpheed-Claws) to version 3.3.1 (Claws).

The upgrades did not solve my problem, but Eric's suggestion worked perfectly:

  --------------------------------
  "You probably need to do this: When composing, go to Edit,
  hover over the undo option (or whichever one has the s key
  as the shortcut), and hit delete to get rid of the shortcut."
  --------------------------------

When I looked at the Edit menu, these was a "S" on the Undo menu item ; hovering the mouse pointer there, and hitting the delete key removed it, as Eric instructed!

Thanks for the other (general) comments, and for taking the time to reply.

Sincerely, Greg  :-)

-----------  Beginning of quoted message:  -----------

On 2008 May 18 (Sun) 08:32 Paul <claws@***> wrote:

Re: Help - lowercase "s" key now deletes text in Sylpheed mail composer

On Sun, 18 May 2008 02:06:56 -0400
Greg wrote: 

> Lowercase "s" key doesn't work ...
> 
> Hello - All of a sudden my lowercase "s" key doesn't work when composing messages using Sylpheed-Claws (v.2.6.0, on Ubuntu 6.06 LTS). Every time I
> type a lowercase "s", it "undoes" / deletes text, recursively each time the "s" key is pressed. It's only the lowercase "s" key, as far as I know.
> 
> I did some Ubuntu system updates today (6.06 LTS, via the update manager) -  this may be related, though I can't see why ...
> 
> Any ideas?  

See Eric's response - this is 'user error', you have set 's' as a hotkey.

Also, subject says 'Sylpheed', this is a mistake, Sylpheed is not Claws Mail!

Thirdly, Sylpheed-Claws is the old, old name for Claws Mail. Version 2.6.0 was the last version known as Sylpheed-Claws, it was released in November 2006, and there have been 18 releases since then!

See [http://www.claws-mail.org/downloads.php](http://www.claws-mail.org/downloads.php) for details on where you can find the latest version of Claws Mail packaged for ubuntu. Upgrading is highly recommended!

best regards

Paul

-- 
It isn't worth a nickel to two guys like you or me, 
but to a collector it is worth a fortune 

---------------------------------------------------------------------
To unsubscribe, e-mail: [email]claws-mail-users-unsubscribe@dotsrc.org[/email]
For additional commands, e-mail: [email]claws-mail-users-help@dotsrc.org[/email]

-----------  End of quoted message  -----------

 ========================================

---

