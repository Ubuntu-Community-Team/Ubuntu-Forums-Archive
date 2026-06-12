---
title: "How do I set a file type to open in a snap application by default?"
date: 2022-01-30
forum: General Help
---

### Post by Paddy Landau on 2022-01-30
How can I set the default app for a file type to a snap application?

I have Adobe Reader, installed via snap. So, I can run Adobe Reader from the menu or from the command line (snap run acrordrdc).

I can also open a file directly from the terminal:
snap run acrordrdc filename.pdf

I want to set the file type PDF to open in Adobe Reader by default. That is, I want to be able to double-click a PDF file and have it open in Adobe Reader.

The standard way to make this setting is to right-click any PDF file > Properties > Open With > [select the required application] > Set as default.

Unfortunately, Adobe Reader isn't in the list of applications, so I can't set it as the default.

Do you know how I can set Adobe Reader as the default app for PDF files, please? I've searched, and found answers that frankly don't make sense to me, so I can't even try them.

EDIT: I use Ubuntu 20.04 (with Gnome)

Thank you

---

### Post by KBar on 2022-01-30
Do you have the *Use a custom command:* field in the *Open With* dialog? Perhaps you could click on *Browse* and point to its binary in *~/snap/acrordrdc* or something like that? I don't use snaps, so I'm sorry if that doesn't help you at all.

---

### Post by deadflowr on 2022-01-30
File associations only work if the Desktop Launchers .desktop file's Exec key has a proper field code included.
I would copy the desktop file from the /var/lib/snapd/desktop/applications directory to my ~/.local/share/applications directory
then I would open in text editor and add %f or something to the end of the Exec command and save.
After that it should show in the open with dialogs, at least for that one user.

More on the Exec key and such: [https://specifications.freedesktop.org/desktop-entry-spec/1.1/ar01s06.html]("https://specifications.freedesktop.org/desktop-entry-spec/1.1/ar01s06.html")

---

### Post by KBar on 2022-01-30
I've just installed *acrordrdc* to test it and can see it in the list (no extra steps required, "it just works"):

---

### Post by Paddy Landau on 2022-01-30
> **KBar said:**
> Do you have the *Use a custom command:* field in the *Open With* dialog?
No, I don't. I realise in hindsight that I should have specified that I use Ubuntu 20.04 (with Gnome).
> **deadflowr said:**
> … copy the desktop file from the /var/lib/snapd/desktop/applications directory to my ~/.local/share/applications directory
… open in text editor and add %f…
That worked! Thank you :-)
> **KBar said:**
> I've just installed *acrordrdc* to test it and can see it in the list (no extra steps required, "it just works"):
It looks as though you're using XFCE. It doesn't work on Gnome, it seems.

---

### Post by KBar on 2022-01-30
> **Paddy Landau said:**
> It doesn't work on Gnome, it seems.

One more reason to ditch GNOME… :biggrin:

---

### Post by Paddy Landau on 2022-01-30
> **KBar said:**
> One more reason to ditch GNOME… :biggrin:
Well, each to his own. I enjoy Gnome.

---

