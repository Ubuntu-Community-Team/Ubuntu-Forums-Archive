---
title: "Acrobat Reader"
date: 2006-12-20
forum: General Help
---

### Post by AllanP on 2006-12-20
I installed Acrobat Reader via Automatix; which worked fine. the only problem is that I have to agree to the Adobe lisense agreement every time i open a PDF file. I tried to find the agreement and agree to it once and for all but, couldn't. Any solution out there?

---

### Post by canadianwriterman on 2006-12-20
Mmmm. Never had that happen. Try uninstalling Acrobat Reader through Automatix and then reinstalling. See if that helps.

---

### Post by arnieboy on 2006-12-21
> **AllanP said:**
> I installed Acrobat Reader via Automatix; which worked fine. the only problem is that I have to agree to the Adobe lisense agreement every time i open a PDF file. I tried to find the agreement and agree to it once and for all but, couldn't. Any solution out there?

try this:
```
rm -rf ~/.adobe
```
and then run acrobat again. you should get the license agreement once and after that it shouldn't come up again.

---

### Post by scrooge_74 on 2006-12-21
Try downloading it directly from adobe site, never had any problems that way, it evens open inside Firefox

---

### Post by arnieboy on 2006-12-21
> **scrooge_74 said:**
> Try downloading it directly from adobe site, never had any problems that way, it evens open inside Firefox

The issue does not have to do with where it was downloaded from. Its got more to do with broken personal data (a permissions issue perhaps? we will soon see.)

---

### Post by AllanP on 2006-12-21
> **arnieboy said:**
> try this:
```
rm -rf ~/.adobe
```
and then run acrobat again. you should get the license agreement once and after that it shouldn't come up again.

Thanks but, nope. Returns to the prompt.

---

### Post by arnieboy on 2006-12-21
> **AllanP said:**
> Thanks but, nope. Returns to the prompt.
Are you running Ubuntu as a user different from the one which installed Acrobat Reader?

---

### Post by AllanP on 2006-12-21
> **arnieboy said:**
> Are you running Ubuntu as a user different from the one which installed Acrobat Reader?

No; I am the only user and pretty much default in all aspects. I just thought maybe there was a file I could edit and do a "Yes" to the License.

---

