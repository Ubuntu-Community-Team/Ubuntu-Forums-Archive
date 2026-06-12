---
title: "Removing several lines from a text file"
date: 2013-04-14
forum: General Help
---

### Post by vasa1 on 2013-04-14
I have a small text file, test.txt, like this:

line 1
line 2
line 3
pattern1
line 4
line 5
line 6
pattern2
line 7
line 8
line 9

I want to remove the text starting with **pattern1** and ending with **pattern2**. Both patterns are unique but the number of intervening lines and their content may vary. How do I do so?

I tried:
```
perl -p -i.bak -e 's/pattern1.*pattern2//s' test.txt
```
because I read that use of the second "s" would allow "." to include line returns but this doesn't work. There are no error messages. I just get back the prompt and the file is unchanged and is the same as text.txt.bak.

In case it matters, I'm using Lubuntu 12.10 without any special programming software installed.

---

### Post by MG&amp;TL on 2013-04-14
I *knew* I'd done this before. From [http://stackoverflow.com/questions/1996585/remove-lines-which-are-between-given-patterns-from-a-file-using-unix-tools](http://stackoverflow.com/questions/1996585/remove-lines-which-are-between-given-patterns-from-a-file-using-unix-tools):

```
sed '/pattern1/,/pattern2/d' < test.txt
```

worked pretty well. :)

---

### Post by vasa1 on 2013-04-14
> **MG&TL said:**
> I *knew* I'd done this before. From [http://stackoverflow.com/questions/1996585/remove-lines-which-are-between-given-patterns-from-a-file-using-unix-tools](http://stackoverflow.com/questions/1996585/remove-lines-which-are-between-given-patterns-from-a-file-using-unix-tools):

```
sed '/pattern1/,/pattern2/d' < test.txt
```

worked pretty well. :)

Yes, it does :) but can you help me run that on several files with the same suffix in a folder and with each file being backed up?

---

### Post by MG&amp;TL on 2013-04-14
> **vasa1 said:**
> Yes, it does :) but can you help me run that on several files with the same suffix in a folder and with each file being backed up?

Great. :)

Well, to simulate your situation, I made a folder called 'test', containing files 'test1.txt', 'test2.txt', and 'test3.txt', which had the contents you posted before. Then I used a for-loop to run the command on all of them:

```
for files in $(find test -name '*.txt'); do sed '/pattern1/,/pattern2/d' < "$files" > "$files.bak"; done
```

Which resulted in the files test1.txt.bak, test2.txt.bak, and test3.txt.bak with the required output in them. :)

Command run-down:
```
for files in $(find test -name '*.txt');
```

Find all the files in 'test' that end with .txt, then iterate over each $files. This should be tweaked for you directory name and file extension.

```
do sed 's/pattern1/,/pattern2/d' < "$files" > "$files.bak";
```

Our original command, but we've substituted our $files from before. Change '.bak' to your preferred file backup extension.

```
; done
```

End our for-loop. 

Hope that helps!

---

### Post by Vaphell on 2013-04-14
```
for files in $(find test -name '*.txt');
```
won't work in case of whitespaces in names


```
while read -rd $'\0' f
do
  sed ...
done < <( find test -iname '*.txt' -print0 )
```
this one is recursive (looks in the whole subtree), in case of files in a single dir *for f in dir/*.txt; do ....; done* will do

---

### Post by prodigy_ on 2013-04-14
Since the question was about Perl: ```
perl -i.bak -ne 'if (/pattern1/){$p=1} if (/pattern2/){$p=0;next} print if not $p' test.txt
```

---

### Post by vasa1 on 2013-04-14
@MG&TL, yes, that does it and thanks for the explanation. And Vaphell, thank you too but I've learned to avoid spaces and funnies in filenames.

---

### Post by Vaphell on 2013-04-14
either way looping through the command output/file with *for*-loop is wrong. *While read* is supposed to be used for that.
You never know if you have to use one of your scripts with some files provided by a friend or downloaded off the internet, they might not be named so conveniently. If writing rock solid solution costs you nothing, just do it (Nike TM)

file processing in order of awesomeness:
- native globs   : rock solid but not easy to recurse (unless globstar ** is enabled)
- while read -d \0 .... done < [null-delimited list]  : rock solid
- while read  .... done < [newline-delimited list]  : fails with newlines (legit in filenames), but mostly works due to relative rarity of \n in names
- for f in  [newline-delimited list] ... done   : dirty hack, fails on all whitespaces found in IFS

---

### Post by vasa1 on 2013-04-14
> **prodigy_ said:**
> Since the question was about Perl: ```
perl -i.bak -ne 'if (/pattern1/){$p=1} if (/pattern2/){$p=0;next} print if not $p' test.txt
```

Wow! That works great as well. Just changed test.txt to *.txt. Now to figure out what magic was involved. Most I've done with perl has been of the 's///' type.

---

### Post by prodigy_ on 2013-04-14
It's actually quite simple. Variable ($p) defaults to false. When pattern1 is encountered we set $p to one (true). Then **print if not $p** only prints the line when $p is false. Finally we need **next** to skip the pattern2 line where we set $p back to zero (false).

Also can be done with awk using the same logic.

---

