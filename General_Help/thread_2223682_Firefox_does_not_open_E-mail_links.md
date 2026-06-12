---
title: "Firefox does not open E-mail links"
date: 2014-05-12
forum: General Help
---

### Post by Martin_Kellner on 2014-05-12
When I click an e-mail link in firefox, nothing happens. In Ubuntu's system preferences TB is set as default e-mail client. In firefox, when I try to set the mailto client, TB is not available as an option, neither is Default which according to the instructions on Mozillas help pages would make FF use TB. In other programs such as libreoffice, TB is automatically being used which makes me think this is a FF specific problem.

---

### Post by SeijiSensei on 2014-05-12
Let's see if we can fix the problem manually.  In Edit > Preferences > Applications > mailto, choose the "other" option.  You'll get a file dialog box.  Navigate to the file /usr/bin/thunderbird and select it.

---

### Post by mlnease on 2014-06-12
Hello,

In "Edit > Preferences > ", there is no " Applications > mailto "--at least not in 24.5.0.

---

### Post by llamabr on 2014-06-12
You have to type 'mailto' into the little box.

---

### Post by mlnease on 2014-06-12
> **llamabr said:**
> You have to type 'mailto' into the little box.

Thanks, llamabr, but I'm afraid you've lost me--what little box?  To which post were you replying?

---

