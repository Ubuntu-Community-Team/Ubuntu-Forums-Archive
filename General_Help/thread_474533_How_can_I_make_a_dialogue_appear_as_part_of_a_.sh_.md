---
title: "How can I make a dialogue appear as part of a .sh script?"
date: 2007-06-15
forum: General Help
---

### Post by weblordpepe on 2007-06-15
Hello there.
I'm just thinking about writing a very quick dirty program.
Basically I want to be able to say hit alt-something and have a dialogue pop up, asking for some text.
And then when I type in the name of say a program, it'll throw that into apt-get in the background with gksu prompting for the password.

The idea being:
alt-xx
type in program name
type password
Confirm file size
program installed.

Or has this already been done? Its basically **apt-get install **but without the terminal.

---

### Post by Garyu on 2007-06-15
zenity is the most common way to throw windows at users from shell scripts.

but what you are describing already exists. you have the Add/Remove programs on the Program menu, you have Synaptic package manager, you have Adept, and lots of other package managers... Why invent the wheel all over again?

---

### Post by freakavoid on 2007-06-15
With zenity for example. It's in the repos.

edit: nevermind.

---

### Post by weblordpepe on 2007-06-15
Its not inventing the wheel. I just want a hotkey to install software without any kind of browsing or searching.
Maybe a hotkey for the package manager would be cool.

---

