---
title: "What is &quot;.&gt;&quot; in a Bash script?"
date: 2022-04-20
forum: General Help
---

### Post by Paddy Landau on 2022-04-20
I read [an article]("https://www.techrepublic.com/article/run-a-single-command-on-multiple-linux-machines/") giving a solution to a problem using a Bash script. In the Bash script, it has this line:
```
ssh -n "$host" "$CMD_EXEC 2>&1" | tee -a "/tmp/$(basename "${0}").${host}.>
```
The comment states, "remove `-a` to override the>"

I am mystified what ".>" means. I've experimented in my own script, and, as I predicted, it leads to a syntax error.

Can you shed some light on this, please?

---

### Post by &amp;KyT$0P# on 2022-04-20
My guess is they are using ksh and those lines ending in > are truncated.

---

### Post by Paddy Landau on 2022-04-20
> **halogen2 said:**
> My guess is they are using ksh…
Unlikely, because the script begins with [FONT=courier new]#!/bin/bash[/FONT]

---

### Post by #&amp;thj^% on 2022-04-20
> **Paddy Landau said:**
> Unlikely, because the script begins with [FONT=courier new]#!/bin/bash[/FONT]

+1
my guess is a print instruction for the script.

---

### Post by &amp;KyT$0P# on 2022-04-20
Could have been copy+pasted from nano, which also does ksh-style line display truncation

---

### Post by #&amp;thj^% on 2022-04-20
> **halogen2 said:**
> Could have been copy+pasted from nano, which also does ksh-style line display truncation

very true, the instructions did use nano>>>(the plot thickens). ;)

---

### Post by Paddy Landau on 2022-04-21
> **halogen2 said:**
> Could have been copy+pasted from nano, which also does ksh-style line display truncation
I don't know ksh. What does that truncation do?

It looks like a mistake, but I don't see how to get hold of the author (Jack Wallen). It's strange that he didn't proofread his article.

---

### Post by &amp;KyT$0P# on 2022-04-21
> **Paddy Landau said:**
> I don't know ksh. What does that truncation do?

In interactive sessions, input lines that extend to the right beyond available width are displayed truncated with > and input lines that extend to the left beyond available width are displayed truncated with <

For example, entering this (without running it yet)
```
echo 'This is an extremely long command that is longer than the 80 characters width of this terminal.'
```
and then going to beginning of the command would look like
```
$ echo 'This is an extremely long command that is longer than the 80 characte>
```

---

### Post by ActionParsnip on 2022-04-21
I've actually looked at the link. The command has wrapped around 2 lines. The full command is
```

ssh -n "$host" "$CMD_EXEC 2>&1" | tee -a "/tmp/$(basename "${0}").${host}.> done <<< "$HOSTS"

```

---

### Post by Paddy Landau on 2022-04-21
> **halogen2 said:**
> In interactive sessions, input lines that extend to the right beyond available width are displayed truncated with >&#8230;
Ah, thank you. That might well be the problem!
> **ActionParsnip said:**
> I've actually looked at the link. The command has wrapped around 2 lines. The full command is
```
ssh -n "$host" "$CMD_EXEC 2>&1" | tee -a "/tmp/$(basename "${0}").${host}.> done <<< "$HOSTS"
```
Hmm, I disagree. That doesn't seem right for two reasons.

[LIST]
[*]"done" should align with "do" three lines above. If it's on the same line as you suggest, there is no "done" corresponding to the "do" which would give a syntax error.
[*]There is a missing double-quotation.
[/LIST]
The explanation by @halogen2 looks likely.

EDIT: The comment beginning "loop over" also has the ">" at the end.

---

### Post by wyattwhiteeagle on 2022-04-21
At the link, he is using nano to edit the script.

In nano, if a line...any line...goes past the width of the terminal, it replaces the exceeding portion of that line with a ">".
It's a default setting for the terminal to display the '>' character.

He just copy-and-paste the terminal output into the article.
and so putting the '>' character into the script and running the script will return the error.

The rest of those line's are needed to acheive the desired result.
You can use the following to get the full lines of the whole script and copy-and-paste into your chosen text editor...
```
sudo <text editor> </path/to/filename>
```
make your desired changes

Then on the first file, use sudoedit and copy-and-paste your text into the terminal to replace what is in the terminal.
after that, hit ctrl+x, then hit y, then hit enter.
(of course I already know that you know what you're doing when using nano to make changes)

I didn't see any way to let the author know about the issue in his article.
Though he does have links next to his avatar image for facebook, linkedin, twitter, and mail.

---

### Post by Paddy Landau on 2022-04-21
> **wyattwhiteeagle said:**
> At the link, he is using nano to edit the script…
Thank you. I don't use nano, so I didn't know about that.

---

### Post by wyattwhiteeagle on 2022-04-21
> **Paddy Landau said:**
> Thank you. I don't use nano, so I didn't know about that.

You're very welcome :)

---

### Post by TheFu on 2022-04-21
> **Paddy Landau said:**
>  It's strange that he didn't proofread his article.

Sometimes the author doesn't have control over the publishing format and mistakes created by local editors.  A few of my online articles inserted errors that were not in my original, submitted, articles.  Because of my contract, I was able to post and maintain copies of the articles on my platform, but there isn't any way to update what was previously published. Many of those publishers are about volume and put out 20 articles a day, every day, for years.

I don't have an answer. Quick searches didn't find anything. It easily could have been a punctuation editor 'fix', but in the wrong location.

---

### Post by Paddy Landau on 2022-04-22
> **TheFu said:**
> Sometimes the author doesn't have control over the publishing format and mistakes created by local editors.
That's a good point.

I think that I'll leave this for now. My original question has been answered :)

---

