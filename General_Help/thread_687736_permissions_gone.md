---
title: "permissions gone?"
date: 2008-02-04
forum: General Help
---

### Post by TechMansoor on 2008-02-04
What in the world happen???????

All of a sudden with my user, I can't do anything. I can't log into a network via a wired or wireless connection, edit services, edit almost anything that is in the Administration side within gnome.

Things I've tried:

I'm guessing this is spanning from a permission issue possibly. I went ahead and added my user under the sudoers file I believe, "visudo, mansoor =All(All) etc..)

Ive tried a couple things as well as like adding myself to the admin and root group which I was already apart of huh..

What could have triggered all of this?

---

### Post by bernied on 2008-02-04
It would be helpful if you could post some examples of what you've tried and what the response was.

If you are adding yourself to groups, you need to log out, then back in again, before this will take effect.

How did you add yourself to those groups (that you were already a member of)?

If you used your current user as the first user when you installed, then you would already have been able to use sudo. I wonder if your sudoers file has been damaged?

---

