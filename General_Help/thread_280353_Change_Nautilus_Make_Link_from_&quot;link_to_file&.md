---
title: "Change Nautilus Make Link from &quot;link to file&quot; to &quot;link_to-file&quot;"
date: 2006-10-19
forum: General Help
---

### Post by jsandys on 2006-10-19
How can I change Nautilus Make Link from creating links with the name, link(space)to(space)filename to the more unix like, link(underscore_or-dash)to(underscore_or-dash)filename?

link to mypicture.jpg should be link_to_mypicture.jpeg or link-to-mypicture.jpg

Is there a Nautilus conf file where this behavior is defined?

The current space-in-the-file-name behavior causes some of my scripts to fail, no such file "to".

Why did the Nautilus designers use the evil space in the file name in the first place?

-- Jeff

---

### Post by jsandys on 2006-10-21
-bump-
This seems like a bug to me, Nautilus is making bad file names and there is no way to fix it.

---

### Post by humptybump on 2007-11-14
This is basically my same question so rather than a new post, I will add here.

When I drag the URL address from Firefox to my desktop or to a folder, it prefixes the page title with "Link to ". How do configure Nautilus, Gnome, or Firefox to remove this prefix ?

---

### Post by JasonF on 2007-11-14
> **jsandys said:**
> -bump-
This seems like a bug to me, Nautilus is making bad file names and there is no way to fix it.

Your scripts should probably be written to support file names with spaces, which is perfectly valid. Try enclosing the filenames in quotes. Eq if a script is called with a filename in $1 use it as "$1".

---

### Post by axel112 on 2008-03-11
-bump-

I'm also wondering if there is an easy way of changing the default name "Link to" to for example "link_to". Hoping there is someone out there who can point me to the right .conf-file to change this.

/axel

---

### Post by pelle.k on 2008-06-12
I will make it my primary goal in life to solve this problem. This is really getting under my skin. Why a distasteful prefix (using whitespace btw) at all?
Maybe we should report this as a (critical!!) bug in gnome's bugtracker? ;)

---

### Post by guraknugen on 2008-07-19
> **pelle.k said:**
> I will make it my primary goal in life to solve this problem. This is really getting under my skin. Why a distasteful prefix (using whitespace btw) at all?
Maybe we should report this as a (critical!!) bug in gnome's bugtracker? ;)

It's already reported, click [here]("http://bugzilla.gnome.org/show_bug.cgi?id=534432").


Vänliga hälsningar (kind regards)
Johnny Rosenberg

---

