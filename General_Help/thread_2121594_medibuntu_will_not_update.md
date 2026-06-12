---
title: "medibuntu will not update"
date: 2013-03-02
forum: General Help
---

### Post by unisol on 2013-03-02
I installed medibuntu into my repositiories, but it refuses to update. Do I need a key?

---

### Post by matt_symes on 2013-03-02
Hi

Opan a terminal and type

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

Post back any error messages here.

Kind regards

---

### Post by unisol on 2013-04-08
I still receive the message that some packages were not installed.

---

### Post by cortman on 2013-04-08
You'll need to post the full output of the previous commands including the errors, before we can suggest anything more.

---

### Post by unisol on 2013-04-15
W: Some index files failed to download. They have been ignored, or old ones used instead. this is the message I get.

---

### Post by cortman on 2013-04-15
How did you add the repository? Please post the full output of

```
cat /etc/apt/sources.list
```

and

```
ls /etc/apt/sources.list.d/*
```

---

