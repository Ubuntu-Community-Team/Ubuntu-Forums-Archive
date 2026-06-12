---
title: "Opera mail opens pdf attachments with Fileroller"
date: 2008-02-16
forum: General Help
---

### Post by robc02 on 2008-02-16
The title says it - and when Fileroller opens it says "Archive type not supported"!

In Opera I have, under" tools, preferences, advanced, downloads", set "mime type" -  application/pdf : pdf to open with Evince. Still no luck. 

.doc attachment open with Open Office, but odt attachments don't - they also open with Fileroller! I haven't noticed any other problems so far. 

Does anyone know where Opera stores information about what default programs it uses to open attachments or downloads? I thought I knew but obviously I am missing something.

---

### Post by robc02 on 2008-02-22
I tried uninstalling Fileroller and the pdf and Openoffice attachments opened correctly, with Evince and Open Office respectively - so Opera is able to sort this out in some circumstances. The problem seems to be that the first mention of "Content Type" in the email header says "multipart/alternative" and the file /usr/share/applications/defaults.list has a line:

multipart/x-zip=file-roller.desktop

I presume this line is the first match found and so File-roller is used.

However, there is still an inconsistency in that doc files open with Open Office despite the first "Content Type" being "multipart/alternative".

Can anyone shed any light on this?

---

### Post by yupie on 2008-05-10
Attachments with the mime-type application/octet-stream should be opened with "gnome-open". But in Opera (Ubuntu?) it defaults to "file-roller". Unfortunately the settings of this mime-type cannot be changed and will be ignored in Opera.

Solution
Create the file /home/[name]/.local/share/applications/defaults.list with the following content:

```
[Default Applications]
application/octet-stream=gnome-open.desktop;
```

Restart Opera

---

### Post by robc02 on 2008-05-10
That works a treat. Thank you.

---

