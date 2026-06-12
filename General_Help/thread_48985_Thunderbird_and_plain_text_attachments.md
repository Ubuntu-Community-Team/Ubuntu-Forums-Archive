---
title: "Thunderbird and plain text attachments"
date: 2005-07-14
forum: General Help
---

### Post by Harderlump on 2005-07-14
Usualy, Thunderbird sets a Content-Type line for an outgoing
message, like this:

```
Content-Type: text/plain; charset=ISO-8859-15; format=flowed
```

But, if I have an attachment of type text/plain, the charset tag is
missing for that part of the multipart:

```
Content-Type: text/plain;
 name="text.txt"
```

Since Ubuntu is optimized for Unicode, the attached text is probably
Unicode. My Boss uses an older system with Mozilla Email, and got
the characters displayed the wrong way.

I guess there should be a configuration option in Thunderbird to specify
a default for plain text attachments, but I didn't found one.

Yes, there is the default encoding option for incoming and outgoing mail,
but it seams they are not used for attachments.

Does anyone know how that could be solved?

MfG Harderlump

---

