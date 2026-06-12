---
title: "Bash: How to fool an app into thinking that it's writing to stdout?"
date: 2021-02-06
forum: General Help
---

### Post by Paddy Landau on 2021-02-06
I have a bit of a problem. I want to access the output from flatpak and parse it in a Bash script.

Here are the first lines of output that I want:
```
[COLOR=#b22222]$[/COLOR] flatpak list
**Name                                              Application ID                                                Version            Branch          Installation**
Dropbox                                           com.dropbox.Client                                            115.4.601          stable          system
FontFinder                                        io.github.mmstick.FontFinder                                  2.0.0              stable          system
Freedesktop Platform                              org.freedesktop.Platform                                      20.08.3            20.08           system
```
So far, so good. If I enter that command in a Bash script, that's exactly what is displayed.

But look what happens if I run the command through a pipe:
```
[COLOR=#b22222]$[/COLOR] flatpak list | head --lines=3
Dropbox    com.dropbox.Client    115.4.601    stable    system
FontFinder    io.github.mmstick.FontFinder    2.0.0    stable    system
Freedesktop Platform    org.freedesktop.Platform    20.08.3    20.08    system
```
The header has been removed, and the formatting has been altered. I don't want that to happen!

I get the same results with this command:
```
[COLOR=#B22222]$[/COLOR] LISTING="$( flatpak list )" ; head --lines=3 <<<"${LISTING}"
```
… And with this command:
```
[COLOR=#B22222]$[/COLOR] flatpak list >listing ; head --lines=3 listing
```
I see nothing in the flatpak commands that allow me to force flatpak to use the human-readable listing. So, I'd like to fool flatpak into thinking that it's writing to stdout instead of to a pipe or a file.

(I actually had this same problem with another command a while ago, but I don't remember which command it was.)

How can I do this, please, or do you have a better solution for me?

---

### Post by TheFu on 2021-02-06
```
echo "Name         Application ID                  Version            Branch          Installation
$LISTING" | column -t
```
will do wonders.

---

### Post by Paddy Landau on 2021-02-06
> **TheFu said:**
> ```
echo "Name         Application ID                  Version            Branch          Installation
$LISTING" | column -t
```
will do wonders.
Thank you! That's pretty good. Some fields have spaces, but fortunately flatpak uses tabs to separate columns, so the following works well:
```
flatpak list | column -t -s $'\t'
```
It still excludes the heading, but I can work around that.

Until someone can tell me how to force flatpak to output the way I want it, I'll use column. (I love the way that Linux always has a solution!)

---

### Post by TheFu on 2021-02-06
That's why the 'echo' command is the first part sent through the pipe to column., to put the headers back.

---

### Post by Paddy Landau on 2021-02-06
> **TheFu said:**
> That's why the 'echo' command is the first part sent through the pipe to column., to put the headers back.
Ah. That should have been obvious to me! Thanks

---

### Post by Keith_Helms on 2021-02-06
Maybe a dumb question, but is it possible the headings are written to stderr?

Try this and see what happens

```
flatpak list 2>&1 | head --lines=3
```

---

### Post by TheFu on 2021-02-06
Not a bad idea, but many CLI tools alter their output if there isn't an interactive shell calling them. There are many ways that can be tested.  Then there are other "new" programs that simply have programming teams who don't consider pretty output needs.

Look at the difference between **route -n** and **ip route**  One makes pretty output, then there is 'ip'.  I've never used flatpak and don't have any need for that subsystem to be installed anywhere, but they do have a --noninteractive switch. Wonder how that was enabled without direct request?

---

### Post by Paddy Landau on 2021-02-07
> **Keith_Helms said:**
> … is it possible the headings are written to stderr?
I hadn't considered that, but no, it doesn't go to stderr. Thanks for the idea.

---

