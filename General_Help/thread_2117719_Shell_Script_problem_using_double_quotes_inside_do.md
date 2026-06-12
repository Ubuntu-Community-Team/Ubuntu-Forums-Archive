---
title: "Shell Script problem using double quotes inside double quotes and storing in variable"
date: 2013-02-19
forum: General Help
---

### Post by sanjay singh on 2013-02-19
Hi,
    I have a problem in using double quotes inside double quotes as follows:--
        **s1="-r printer:sanjay=\"HP LaserJet 1018\""**

  Whenever i am using the **value of variable s1** inside command as follows:--
        ** rdesktop -u administrator -p admin_ $s1_ ip-address**

   the command is not executing as expected..

But if i am writing it directly like:--
**rdesktop -u administrator -p admin -r printer:sanjay="HP LaserJet 1018"ip-address**

its working fyn..

plz help me to getting out of this stuff..

---

### Post by SeijiSensei on 2013-02-19
Run
```
echo "rdesktop -u administrator -p admin $s1 ip-address"
```
and see how it is parsed.

Using escaped quotes usually works, but you could try using single-quotes in the initial declaration instead:
```
s1='-r printer:sanjay="HP LaserJet 1018"'
```
since there are no variables to expand.

---

### Post by schragge on 2013-02-20
The problem is the quotes are retained after expanding $s1, but the value of $s1 gets word-splitted nevertheless.
What you get after expanding $s1 is equivalent to
```

rdesktop -u administrator -p admin -r 'printer:sanjay="HP' LaserJet '1018"' ip-address

```
Instead, try
```

eval rdesktop -u administrator -p admin $s1 ip-address

```

Or use zsh instead of bash.

BTW, are you sure a space is always required between the name and the value of an option for rdesktop? If not, you can also get away with
```

s1='-rprinter:sanjay="HP LaserJet 1018"'
rdesktop -u administrator -p admin "$s1" ip-address

```

---

### Post by cariboo on 2013-02-22
Move to General Help, as this has nothing to do with Ubuntu Application Development.

---

