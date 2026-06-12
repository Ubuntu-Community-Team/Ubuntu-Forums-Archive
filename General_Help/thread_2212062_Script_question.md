---
title: "Script question"
date: 2014-03-19
forum: General Help
---

### Post by Korkel on 2014-03-19
Hello,

I'm making a script for myself to install a spefic program. Before it starts you will see some texts, is there a way that you must [Enter] to continue?

After everything is installed, the terminal closes itself, how can I keep it open?

Thank you.

---

### Post by varunendra on 2014-03-19
Add a "read" command in the last.

Edit: To elaborate, something like this -
```
printf "\n All Done ! Press 'Enter' to exit.."
read
```

---

### Post by Korkel on 2014-03-19
> **varunendra said:**
> Add a "read" command in the last.

Edit: To elaborate, something like this -
```
printf "\n All Done ! Press 'Enter' to exit.."
read
```
Did that, but script closes automatic.

---

### Post by varunendra on 2014-03-19
If you added it as the last lines of the script and it still exits automatically then something maybe wrong in the script causing it to exit without finishing properly. Means - the execution never reaches those proposed lines.

You may add extra lines containing "read" command to determine exactly which steps are finishing properly. You might as well post the script itself here so we can see if there are any obvious culprits.

---

