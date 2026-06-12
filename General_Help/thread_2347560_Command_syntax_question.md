---
title: "Command syntax question"
date: 2016-12-26
forum: General Help
---

### Post by SchnappiJedi on 2016-12-26
Hi,

Is...

```
cp -p -r -v -u /source /destination
``` 

the same as

```
cp -prvu /source /destination
```

---

### Post by DuckHook on 2016-12-26
&#8230;yes it is.

---

### Post by Keith_Helms on 2016-12-26
Options that require a value usually need to be specified separately or at least last.   Options that don't require a value can be specified either separately or together.

---

### Post by SchnappiJedi on 2017-01-03
Thanks. Going off this how can one add a non executable comment (or comments) into a given command?

---

### Post by Keith_Helms on 2017-01-03
Depends on what you mean by "into".  When running a command from the terminal or a script, you can add a comment following the command by using a hashmark (#).

```
ls -l # show my directory
```

---

### Post by SchnappiJedi on 2017-01-03
For example say forget what -v means (hopefully don't forget that but others especially in rsync, ect would be useful). So the following would work?

```
cp -prvu /source /destination #-v means verbose
```

---

### Post by Keith_Helms on 2017-01-03
Yes that would work.  What would NOT work is something like this:

```
cp -prvu #-v means verbose /source /destination
```

When you said "into" I was afraid you might want something like that.

---

### Post by SchnappiJedi on 2017-01-03
Nope thanks.

---

