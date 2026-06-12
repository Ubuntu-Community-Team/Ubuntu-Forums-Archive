---
title: "awk text processing syntax question,  backslashes"
date: 2007-11-09
forum: General Help
---

### Post by ckuruwita on 2007-11-09
Hi

I am trying to process a text document using the following syntax:
```

cat logs.txt | grep write | awk 'NR!=1 {print}'| awk -v RS="\n" -v ORS="" {print}

```
where the document looks like this

```

document.write("<TEXTAREA cols=70 name=securitylog \'readOnly\' rows=20 wrap=off edit=\'off\'>11/09/2007  23:39:21 xx.xx.xx.xx login success \n11/09/2007  23:37:42 xx.xx.xx.xx logout        \n11/09/2007  23:37:41 xx.xx.xx.xx login success \n11/09/2007  23:36:47 xx.xx.xx.xx logout        \n11/09/2007  23:36:39 xx.xx.xx.xx login success \n11/09/2007  23:33:45 xx.xx.xx.xx logout        \n11/09/2007  23:33:44 xx.xx.xx.xx login success \n11/09/2007  23:33:21 xx.xx.xx.xx logout        \n11/09/2007  23:33:21 xx.xx.xx.xx login success \n11/09/2007  23:33:05 xx.xx.xx.xx logout        \n11/09/2007  23:33:04 xx.xx.xx.xx login success \n11/09/2007  23:31:42 xx.xx.xx.xx logout        \n11/09/2007  23:31:42 xx.xx.xx.xx login success \n11/09/2007  23:31:20 xx.xx.xx.xx logout        \n11/09/2007  23:31:19 xx.xx.xx.xx login success \n11/09/2007  23:29:04 xx.xx.xx.xx logout        \n11/09/2007  23:28:39 xx.xx.xx.xx login success \n06/01/2005  00:01:13 xx.xx.xx.xx logout        </TEXTAREA>")

```

but when i run the command awk interprets the \n as a new line when i actually want the text "\n" not the escape character interpretation

could some body please suggest the correct syntax

thanks :)

---

### Post by kast on 2007-11-09
Not positive, but have your tried.

**```
cat logs.txt | grep write | awk 'NR!=1 {print}'| awk -v RS='"\n"' -v ORS="" {print}
```**

---

