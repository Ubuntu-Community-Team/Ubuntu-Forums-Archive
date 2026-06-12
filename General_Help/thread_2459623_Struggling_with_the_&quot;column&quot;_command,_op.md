---
title: "Struggling with the &quot;column&quot; command, option -c"
date: 2021-03-22
forum: General Help
---

### Post by Paddy Landau on 2021-03-22
I'm using the [FONT=courier new]column[/FONT] command with the [FONT=courier new]-c[/FONT] option to limit the width of the output in the terminal.

My problem is that it seems to ignore the [FONT=courier new]-c[/FONT] option, so no matter what I put in it — a large or small number — it's completely ignored.

According to man column:
```
-c      Output is formatted for a display columns wide.
```
Here is my test code:
```
LISTING=$'Col 1\tCol 2\tLong column three\tCol 4\nLong column 1\tcol 2\tcol 3\tcol 4\n'
column -t -s $'\t' -c 100 <<<"${LISTING}"
```
I can change 100 to 20, 200, whatever, and the output is always exactly the same. I can even put a non-number such as [FONT=courier new]xyzzy[/FONT], and it doesn't complain but still ignores it.

My problem is that the output for some listings exceeds the width of the terminal, so I wish to use [FONT=courier new]${COLUMNS}[/FONT] as the width, as follows, to prevent line-wrapping by truncating columns.
```
column -t -s $'\t' -c ${COLUMNS} <<<"${LISTING}"
```
Is there another solution that I can use? Or do I have to manually program this?

---

### Post by Dennis N on 2021-03-22
> Is there another solution that I can use? Or do I have to manually program this? 
I've not used the column command. For another solution, you can set the default number of columns in the profile (Edit > Preferences > Profiles).  See screenshot.
Also, Terminal Menu has a selection of sizes (these may only be temporary - not sure).

Reference system: Ubuntu 18.04

---

### Post by spjackson on 2021-03-23
> **Paddy Landau said:**
> 
My problem is that the output for some listings exceeds the width of the terminal, so I wish to use [FONT=courier new]${COLUMNS}[/FONT] as the width, as follows, to prevent line-wrapping by truncating columns.

I have never come across the column program. What is it supposed to do? It's unclear to me from the man page. There are many more commonly used tools that can be made to truncate lines, including awk & sed, but my tool of choice here would be cut.
```

cut -c 1-100 < somefile

```
or, if the input contains tabs which would still cause wrapping then 
```

expand < somefile | cut -c 1-100

```
You could use these tools in conjunction with column if column is doing something useful for you.

Another approach would be to use
```

setterm --linewrap off

```
This would simply stop line wrapping rather than truncating at a particular column - if that's what you wanted.

---

### Post by Paddy Landau on 2021-03-23
Thanks for your replies. That's not what [FONT=courier new]column[/FONT] does.

It takes lines of text that have a delimiter (in my case, tab, rather like a CSV file), and formats it as a table, inserting whitespace as necessary to make the columns line up. It doesn't extract anything, but instead "prettifies" it for display.

In my example, I have two lines with 4 columns. As it stands, the output looks like this:
```
Col 1   Col 2   Long column three       Col 4
Long column 1   col 2   col 3   col 4
```
What [FONT=courier new]column[/FONT] does is reformat it like this:
```
Col 1          Col 2  Long column three  Col 4
Long column 1  col 2  col 3              col 4
```
As you can see, it aligns every column.

The problem is when the terminal width is too small, and it should truncate columns to fit.

**Background**

I'm trying to solve a problem with flatpak's display. Flatpak displays its output exactly as I want, but only when it's not put through a pipe — and I have to put its output through a pipe.

I've already asked about this elsewhere (how to fool flatpak into thinking it's outputting to a terminal instead of a pipe), but no one could answer that question. (If you know the answer to that question, it would solve my problem without having to use [FONT=courier new]column[/FONT]!)

---

### Post by The Cog on 2021-03-23
I don't think -c does what you think it does. o 
I think column will normally put a plain list into columns based on the widest item and the width of the screen - it auto-calculates the number of columns it can fit on the screen.
-c overrides the screen width used in the how-many-columns calculation.
-t tells it to work out the number of columns from the input lines and ignore the apparent (or overriden with -c) screen width.

---

### Post by dragonfly41 on 2021-03-23
Can you, perhaps, use aha to create your output .. in html ..

[https://github.com/theZiz/aha](https://github.com/theZiz/aha)

Example from above:

MAN_KEEP_FORMATTING=1 COLUMNS=80 man aha | ul | aha > man-aha.htm
[LIST]
[*]Creates an HTML file with the man page of aha. Man uses nroff's bold and underline, which ul converts to SGR.
[/LIST]


[Added note] In Ubuntu 20.04 libncursesw5 needs to be installed through Synaptic.
I had libncursesw6 and that caused an error. I enabled both 5 and 6.

---

### Post by spjackson on 2021-03-23
> **Paddy Landau said:**
> 

As you can see, it aligns every column.

The problem is when the terminal width is too small, and it should truncate columns to fit.

Fair enough, so as I said earlier...
> 
You could use these tools in conjunction with column if column is doing something useful for you.

e.g.
```

column some_flags_here < some_file | expand | cut -c 1-100

```
or use setterm.

If you want column to truncate the lines without help from any other tools, I'm afraid I can't help you.

---

### Post by Paddy Landau on 2021-03-23
> **The Cog said:**
> I think column will normally put a plain list into columns based on the widest item and the width of the screen..
No, it ignores the width of the terminal. If the terminal is 100 columns wide and the output is 150 columns, *column* puts out 150 columns.
> **The Cog said:**
> -c overrides the screen width used in the how-many-columns calculation.
That's what I understood, but it doesn't do this.
> **The Cog said:**
> -t tells it to work out the number of columns from the input lines and ignore the apparent (or overriden with -c) screen width.
So, then, I don't understand the point of -c. If I use it without -t, it doesn't work for me.
> **dragonfly41 said:**
> Can you, perhaps, use aha to create your output .. in html ..
That's an interesting idea! But I'm not sure how to then convert back into text for the terminal. If I'm processing the input anyway to convert to HTML, I might as well just process it to the required output.
> **spjackson said:**
> ```
column some_flags_here < some_file | expand | cut -c 1-100
```
Well, that would truncate the output, but unintelligently, so that everything at the end is truncated.

Thanks for all of your help.

I think that I'll just create a script to process the output into the right width. It's a bit of a bother, but nothing difficult.

I just wish that I could fool flatpak into thinking that it's writing to a terminal, because its developers made an assumption about its use (I hate when developers just assume things).

---

### Post by The Cog on 2021-03-23
While we agree column is not the tool for your job, here is my understanding of how column works. It's easy to see with a simple list such as the output from **ls**.Try this full-screen:
**ls | cat** outputs filenames one per line (| cat is needed to stop it doing its own column layout)
**ls | column** will put the lines into columns, filling the terminal, using as many columns as will fit across the screen.
**ls | column -c 80** will print in as many columns would fit in an 80 wide screen (2 columns in my case but it depends on the longest line)
**ls | column -c 120** will print more columns, maybe twice as many
basically, column count = screen width / (widest item + 1 space)
It never truncates entries, but will pad short ones to match the longest, and adds newlines after the calculated number of columns.
**-t** gets it to count the number of columns from the format of the the input lines rather than from screen width, which is useful for padding data that is already in columns. 

Hope that's right. It does take some trial and error to figure out what it is doing, that's for sure.

---

### Post by Paddy Landau on 2021-03-24
> **The Cog said:**
> … here is my understanding of how column works.
Thank you for such a clear explanation! I finally understand what's going on with *column*!

I shall indeed take another approach with this.

I'll mark this thread as solved.

---

