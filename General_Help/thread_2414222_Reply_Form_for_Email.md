---
title: "Reply Form for Email"
date: 2019-03-07
forum: General Help
---

### Post by asearle on 2019-03-07
I currently use both "Thunderbird" and "Evolution" as Email programmes (Lubuntu 16.04) and was wondering whether anyone has experience of creating, sending and receiving "Reply Forms"?

The idea that I have is that (using HTML) I would incorporate some (input) fields which the recipient should fill out and then send back as a reply.

I have tried adding an HTML input-field to an Email but, although it appears correctly, it seems to always disappear as soon as I want to enter some data.

The other thing that I would like to know is whether the values entered by the recipients will remain stored in the email reply? (i.e. to be retrieved by the original sender when they get the reply).

If anyone has tried this or has any tips for me, then that would be a great help.

Or maybe there are other, easier methods? Maybe using PDF-Forms?

Many thanks,
Alan

PS: Maybe I need to add <FORM> declarations around the input fields?

---

### Post by dragonfly41 on 2019-03-07
I will throw in one idea .. but it might be overkill.

It is to explore [Orbeon Forms]("https://www.orbeon.com/") which implements xforms.
Form Runner allows easy design of xforms.

You will need to grapple with installing Orbeon war on a tomcat server.

Here is just one reference to email server.

[https://eadministracio.upc.edu/orbeon/doc/processors-messaging-email](https://eadministracio.upc.edu/orbeon/doc/processors-messaging-email)

But refer to Orbeon tutorials first before deciding if it is worth the effort.

---

### Post by SeijiSensei on 2019-03-07
E-mail protocols don't really support what you're trying to do.  Your best bet would be a web application that handles forms.  I write things like that from scratch in PHP, but I'd bet there are lots of ready-made solutions that you might adapt.

The HTTP protocol knows how to handle input fields through the use of the POST and GET methods in the protocol. (Any [Google search]("https://www.google.com/search?client=ubuntu&channel=fs&q=forms+via+email&ie=utf-8&oe=utf-8") shows how the GET protocol is implemented with multiple field=value pairs after the "?" in the URL.)  E-mail has none of that. You might be able to send simple plain-text questionnaires with replies directed to a script for processing. But just putting an HTML <FORM> in an email won't solve the problem.

How about [Google Forms?](https://www.google.com/forms/about/)

---

### Post by asearle on 2019-03-07
Many thanks for your feedback on this.

I need to do this without external infrastructure so the server-based solution is out (but many thanks anyway).

But Seijisensi, you have prompted me to have one thought: A form can be set to send an email (I believe) so, if I had fields in the email inside a HTML Form then couldn't that form send the results? The form would pick up the content for the email from the form-fields declared.

However, this would need to work without server-based coding.

I'll investigate and give feedback.

Many thanks for your feedback.

Yours,
Alan

---

### Post by asearle on 2019-03-07
I made some very interesting discoveries on this topic ...

I used this code ...

[https://www.w3schools.com/html/tryit.asp?filename=tryhtml_form_mail]("http://https://www.w3schools.com/html/tryit.asp?filename=tryhtml_form_mail")

... to create a form for the entries.

Opened in a browser (with no backend-processing) it works fine and, when you click on send, creates a "skeleton" email containing just the entries from the form ...

> name=Smith
mail=MyEmail
comment=Comment text

That is pretty much exactly what I want!

So we will generate the HTML-Form which we send as an attachment in an email. The attachment then needs to be opened with a browser, filled out and the user clicks on "Send" to create the skeleton Email. Perfect! We will then programmatically extract the data we require from the received emails.

The one slight disappointment is that editing cannot take place within the Email: If you incorporate the form into the email (as HTML, no problem) and send it to another address, a.) in the Email that you receive you can enter data into the input fields (no problem) and, although the reset button is active, the send button isn't (so you can't send). ... and ... b.) If you hit "reply" and try to enter data the form fields seem to "evaporate". Very strange.

However, the advantage of opening up in a browser is that, if you save the web-page to a local drive, you have a one-to-one copy of the data that you sent so you can/could make adjustments and re-send, if you wanted to.

So, yes, this will fit our needs perfectly.

Hope this helps someone else out there.

Yours,
Alan

---

### Post by SeijiSensei on 2019-03-07
I was thinking more along the lines of something like this:

```

How old are you?
Q1 --> Enter your age here


```

If the message is constructed so that replies go to an email "alias" that pipes the replies to a script, the script could just look for the lines beginning with "Q1" and parse them to build a database of responses.

I tried composing an HTML message in Thunderbird with an embedded form.  I could send the form to myself, but had no way to fill it out and reply.  I tried simply replying to the message, and tried using an HTML <input type=submit> button, but neither approach worked.

---

### Post by asearle on 2019-03-07
We were pondering using raw text (as you suggest) but the users want guided entry.

Yes, it seems to not be possible to edit/reply within the email. But when the attachment is opened in a browser that is no problem. So that is what we plan to do.

Cheers,
Alan

---

