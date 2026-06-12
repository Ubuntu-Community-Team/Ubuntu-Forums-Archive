---
title: "Postfix block email with chinese characters"
date: 2022-05-30
forum: General Help
---

### Post by Anquietas on 2022-05-30
Hello,

We have an email server running Dovecot and Postfix.

I recieve a lot of spam email containing wierd chinese/japanese or other asian characters.

We don't need these emails in our organization and we do not communicate with people using asian characters.

How can we instruct Postfix to block out all emails containing asian characters ?

We already use "body_checks" to discard email containing some regex strings... but how can we do it for asian characters ?

```

Server [/etc/postfix] # cat body_checks
/free mortgage quote/     DISCARD
/repair your credit/      DISCARD
/From:.*<>/         DISCARD
Server [/etc/postfix] # cat main.cf |grep body
body_checks = pcre:/etc/postfix/body_checks
Server [/etc/postfix] #

```

---

### Post by TheFu on 2022-05-30
There is a charset field in the header. Use a regex to match on the character sets you don't want and DISCARD or REJECT those.
We use the header_custom file for that. it is referenced in the main.cf
smtp_header_checks = pcre:/etc/postfix/header_custom pcre:/etc/postfix/header_smtp

We do a few other header checks too for extremely old User-Agents and block those since anyone using 15 yr old mailers are obviously spammers.

---

### Post by Anquietas on 2022-07-28
OK, and how do I do that ?
Technically, please explain the steps...

Also, I have discovered that some emails are encoded in Base64. This, effectively, bypasses the checks. How can I check for base64 encoded strings of asian characters ?

---

### Post by #&amp;thj^% on 2022-07-28
I follow this for the most part, I also learn new items as time passes.
[https://www.linuxbabe.com/mail-server/block-email-spam-postfix](https://www.linuxbabe.com/mail-server/block-email-spam-postfix)

---

### Post by Anquietas on 2022-07-29
Thank you for the reply, but I asked something else.
I needed help with a specific problem, not 7 tips to harden my SMTP Server...  (which, by the way, I already did).
I need specific instructions on how to disable asian characters (even if they are encoded in Base64)...

---

### Post by #&amp;thj^% on 2022-07-29
I'm going to +1 this one: [https://www.linuxquestions.org/questions/linux-server-73/postfix-block-email-with-asian-characters-4175712786/](https://www.linuxquestions.org/questions/linux-server-73/postfix-block-email-with-asian-characters-4175712786/)
Your placing far to much on us, Read, Read, Read.
Good Luck though

---

### Post by Anquietas on 2022-07-29
With all due respect, it seems that the Forum is not much help for "read read read".
I came to the forums seeking a proven solution, in case anyone already dealt with this issue.
I do not ask others to read for me ! This is called misjudging. I learned to read when I was 4 :-)
The ideea was to obtain a quick fix IF someone else already encountered the problem - I assume that is also the role of a Forum - to ask quick help, if available :-)
I assume anyone can read :-)
OK, back to reading manuals. Thank you.

---

### Post by Anquietas on 2022-07-29
I have tried - with no result. I always try to solve my problems before posting in the forums. Usually, the forums are the last place to try to ask help, and after all other attempts failed.

The problem is simple: I want to filter asian characters.

Here is my header_checks file:
```

/free mortgage quote/     DISCARD
/repair your credit/      DISCARD

```

Here is my body_checks file:
[https://pastebin.com/mF0VLCzY](https://pastebin.com/mF0VLCzY)

The filtering works great if I test any asian character from the list in the body_checks file.

The problem is that I receive emails which ENCODE with Base64 (the Email client displays the asian character but the Message Source is Encoded in Base64).
For example: &#36899; in Base64 is "6YCj"
And my message source is full of Base64 encoded text.

I have also tried these:
```

/^Subject:.*=\?(?:GB2312|big5)\?/   DISCARD
/^Content-Type:.*\bcharset="?(?:GB2312|big5)\b/   DISCARD
/(?:[a-z0-9]?[\200-\377]){8,}/   DISCARD

```

It gives me the following problem:
```

postmap: warning: header_checks, line 5: unbalanced '"' in '/^Content-Type:.*\bcharset="?(?:GB2312|big5)\b/   DISCARD' -- ignoring this line

```

Also, if I leave these in header_checks, it still doesn't filter the base64-encoded characters...

---

### Post by TheFu on 2022-07-29
```

postmap: warning: header_checks, line 5: unbalanced '"' in '/^Content-Type:.*\bcharset="?(?:GB2312|big5)\b/   DISCARD' -- ignoring this line

```
Seems pretty clear to me.  there is an extra '"' in the line.  Perhaps reading the error would be a good step?

I cannot help with base64. Haven't seen that since the 1990s when we all used uuencode to email binaries around.

---

### Post by #&amp;thj^% on 2022-07-29
> **Anquietas said:**
> 
I do not ask others to read for me ! This is called misjudging. I learned to read when I was 4 :-)
The ideea was to obtain a quick fix IF someone else already encountered the problem - I assume that is also the role of a Forum - to ask quick help, if available :-)
I assume anyone can read :-)

No misjudging, and I'll quote others that have "Tried to help you"  :  [https://www.linuxquestions.org/questions/linux-server-73/postfix-block-email-with-asian-characters-4175712786/](https://www.linuxquestions.org/questions/linux-server-73/postfix-block-email-with-asian-characters-4175712786/)
> You're essentially asking others to read the docs and only pull out the pieces you need, rather than you doing it. If you use the search terms given you to, you'll find examples;
And with all due respect, the forum is here if you're needing HELP...not wanting to read the instructions/claim they're 'hard to understand', etc., and wanting someone else to read them for you doesn't fall within that realm.

I feel TheFu has been very helpful over the norm.

---

