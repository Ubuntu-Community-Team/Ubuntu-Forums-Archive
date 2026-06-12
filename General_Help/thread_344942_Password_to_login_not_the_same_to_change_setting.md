---
title: "Password to login not the same to change setting?"
date: 2007-01-23
forum: General Help
---

### Post by pierre-arnaud on 2007-01-23
Hi everyone,

I'm very new with Ubuntu 6.06 .

Let's say my login name is "1A2" and my password "e4L".

I login. I want to connect to Internet via my house's WLAN. But to access to Networking section in "System", I have to write my password. But the password I wrote during the login doesn't work then.

Maybe there is a problem with my Ubuntu, as I had problems installing it in the first place, so I installed it 3 times; maybe I again made mistakes.

My laptop is an Inspiron 640 m Dell, if ever that is useful to mention.

Thank you very much for your patience,

Arnaud

---

### Post by taurus on 2007-01-23
What groups do you belong to?  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
id
```

---

### Post by pierre-arnaud on 2007-01-23
I am sorry, I do not understand you questions.

Thank you,

Arnaud

---

### Post by taurus on 2007-01-23
If you want to use sudo, you need to belong to groups adm & admin so why don't you paste the output of this command here?

```
id
```

---

### Post by matthewstory on 2007-01-24
He wants you to open a terminal window:

Applications -> Accessories -> Terminal

And type in the command:

id

This command will do the same thing:

groups

And then hit enter . . . and the groups that you are a member of will be printed to the terminal screen . . . he then wants you to copy that stuff (SHFT+CTRL+C) and paste it up in a reply here so that we can see what's going on and help you.  Hope that clears up some of your confusion.

---

