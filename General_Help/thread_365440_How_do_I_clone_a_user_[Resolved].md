---
title: "How do I clone a user? [Resolved]"
date: 2007-02-19
forum: General Help
---

### Post by avihappy on 2007-02-19
I am using the Fiesty Knot 4. I need to clone my primary user so I can use the new account and make it look like Windows (for guests). I have my setting set up PERFECTLY for this computers needs (beryl, session commands) and if I don't use them, my PC becomes unusable. So, how can I clone a user, but give it a different name/password?

---

### Post by dcstar on 2007-02-19
> **avihappy said:**
> I am using the Fiesty Knot 4. I need to clone my primary user so I can use the new account and make it look like Windows (for guests). I have my setting set up PERFECTLY for this computers needs (beryl, session commands) and if I don't use them, my PC becomes unusable. So, how can I clone a user, but give it a different name/password?

I would expect you can just create a new user, and then copy the whole home directory (including the hidden files) from your working user to the new home folder.

The only issue would be any preset passwords etc. in the original account that you didn't want copied across.

---

### Post by avihappy on 2007-02-19
I had tried that, and the whole account got messed up and I had to delete it.

---

### Post by avihappy on 2007-02-19
Drat, Double Post!

---

### Post by aysiu on 2007-02-19
You're on the right track. You copy the whole home directory, but you then have to change ownership of the new copied files and folders.

Let's say your original user is called *avihappy*, and you want the cloned user to be called *avisad*: ```
sudo adduser avisad
sudo cp -R /home/avihappy/* /home/avisad/
sudo chown -R avisad:avisad /home/avisad
```

---

### Post by avihappy on 2007-02-20
Ok wait. It is doing the job. :)

EDIT: Yes, it worked very well. Thank you.

---

