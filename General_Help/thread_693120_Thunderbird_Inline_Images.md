---
title: "Thunderbird Inline Images"
date: 2008-02-10
forum: General Help
---

### Post by dln9 on 2008-02-10
I have a problem with embedded images in Thunderbird emails. I have "View>>Message Body As" set to "Original HTML", and I have "View>>Display Attachments Inline" checked. I am composing emails in HTML mode, and, I use the "Rich Text (HTML) Only" format when creating an email.

I take a screenshot of my desktop, and save that screenshot as a jpg file. Then, in Thunderbird, I create an email. In the email, I click on "Insert>>Image". I locate the jpg file and its location is entered into the box labeled "Image Location:". "Attach this image to the message" is checked. I select "Don't use alternate text". Then, I click "OK", and I can see the image of the jpg file inline in the email I am composing just fine. Then I send this email to myself.

When I open that email in Thunderbird, I cannot see the image inline in the email message. Instead, it is in there as an attachment.  If I send that email to another person who uses Microsoft Outlook 11, he also sees an attachment in the email, instead of seeing the image inline in the body of the email.  

(If I then right click on that message in the Inbox in Thunderbird, and select "Edit as New...", I see a placeholder for the image, but not the image itself.)

What must I do so that I can see images inline in emails I recieve?

I did post this problem I just described for you on the Mozilla Thunderbird forum, but only one person responded with this after I sent him the message header information that apparantly showed that the MIME type that Thunderbird (?) assigned to this image was "application/octet-streams": "The MIME type is totaly wrong for a JPEG image. The valid type is image/jpeg or image/jpg. The application/octet-streams is reserved for executable binaries such as EXE, COM, SCR, etc.

If you were running MS Windows of any flavor the fix would be in it's registry. I do not have a clue how Linux matches MIME types to file types, but that looks like the source of your problem."

Since he didn't have a clue how to fix this problem in Linux, I thought I'd try this forum. Does anyone know what I should do to fix this problem?  

Thanks for any help with this problem.

---

### Post by jken146 on 2008-02-10
HTML belongs on the web, not in emails.

[http://www.georgedillon.com/web/html_email_is_evil_still.shtml](http://www.georgedillon.com/web/html_email_is_evil_still.shtml)

---

