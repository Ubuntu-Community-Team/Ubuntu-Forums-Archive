---
title: "Do I have two packages of Node.js installed now?"
date: 2021-08-18
forum: General Help
---

### Post by stackerito on 2021-08-18
[COLOR=#1A1A1B][FONT=&amp]I had node v10.19.0 and wanted to update it to the latest stable version using the following instructions - [https://askubuntu.com/questions/426750/how-can-i-update-my-nodejs-to-the-latest-version](https://askubuntu.com/questions/426750/how-can-i-update-my-nodejs-to-the-latest-version) :[/FONT][/COLOR]
```
sudo npm cache clean -f
sudo npm install -g n
sudo n stable

```[COLOR=#1A1A1B][FONT=&amp]I also needed to fix the path using the command PATH="$PATH" as suggested by the Node updater:[/FONT][/COLOR]
> [INDENT]Note: the node command changed location and the old location may be remembered in your current shell.
old : /usr/bin/node
new : /usr/local/bin/node
To reset the command location hash either start a new shell, or execute PATH="$PATH"
[/INDENT]
[COLOR=#1A1A1B][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]But, before I changed the paths, it still gave me the output v10.19.0 before I changed the paths. Does it mean I now have two Node packages installed?[/FONT][/COLOR]

---

### Post by TheFu on 2021-08-18
Perhaps. Cannot tell.  For developers of custom software, it is common to have multiple versions of different tools installed.

Think I have 5 versions of perl installed on my development box, but only 1 as part of the APT packages.  That's the "system perl" and I never, ever, touch it. It is needed for the other packages installed by APT.
But different clients need different versions of perl, so I try to have exactly the same version available.

There are multiple ways to install npm, so only you can check each method for a package.  Check apt, snap, flatpak, and manual methods.  There are probably npm-specific version management too.  I don't know.  With perl, there's something called "perlbrew" to install 25+ different versions and allow switching between each different self-contained, perl environment. Python and ruby have similar tools, so Node must have one as well.  Only you can answer the base question.

---

