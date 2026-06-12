---
title: "Replacing backslashes with sed"
date: 2013-01-21
forum: General Help
---

### Post by cbillson on 2013-01-21
getting quite used to sed now, am normally using the follwong command:
 
sed -i "s/test/newdata/g" /path/myfile
 
hae managed by playing around with "" i can replace 'test' with the content of a $variable
 
my latest challenge is to replace 'logs\\' with 'logs/' (quotes not needed)
 
i assume i need to wrap the backslash in some way, but at a loss to how, anyone know how i need to format this?
 
Cheers, Chris

---

### Post by Impavidus on 2013-01-21
Escape the backslash with another backslash, possibly both in sed and in the shell.

If you use single quotes bash won't change \\ into \, so you won't need \\\\ to pass \\ to sed. Sed still needs \\ to match a single \. Its best to not use / as separator if you want / in your output, so these options should work:```

sed -i "s/logs\\\\\\\\/logs\\//g" file
sed -i "s:logs\\\\\\\\:logs/:g" file
sed -i 's/logs\\\\/logs\//g' file
sed -i 's:logs\\\\:logs/:g' file
```I recommend the last one. However, if you want to put a variable in it you still may need the double quotes.

Edit: If logs\\ is in a variable, you won't need to escape the backslashes to prevent processing by the shell. You still need to excape them for sed. In other words: still double the amount of \s:```

string='logs\\\\'
sed -i "s:$string:logs/:g" file

```

---

### Post by Cheesemill on 2013-01-21
You don't have to use / as the field delimiter, you can choose any character you want. In this case I am going to use : instead...
You also need to escape each \ with an extra \.

```
 sed -i 's:logs\\\\:logs/:g' /path/myfile
```

---

### Post by cbillson on 2013-01-21
> **Impavidus said:**
> Escape the backslash with another backslash, possibly both in sed and in the shell.
 
If you use single quotes bash won't change \\ into \, so you won't need \\\\ to pass \\ to sed. Sed still needs \\ to match a single \. Its best to not use / as separator if you want / in your output, so these options should work:```

sed -i "s/logs\\\\\\\\/logs\\//g" file
sed -i "s:logs\\\\\\\\:logs/:g" file
sed -i 's/logs\\\\/logs\//g' file
sed -i 's:logs\\\\:logs/:g' file
```I recommend the last one. However, if you want to put a variable in it you still may need the double quotes.
 
Edit: If logs\\ is in a variable, you won't need to escape the backslashes to prevent processing by the shell. You still need to excape them for sed. In other words: still double the amount of \s:```

string='logs\\\\'
sed -i "s:$string:logs/:g" file

```
 
 
I did not know the seperator was user selectable, this is where i'm going wrong so thanks very much

---

