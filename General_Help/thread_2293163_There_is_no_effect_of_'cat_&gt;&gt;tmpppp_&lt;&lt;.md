---
title: "There is no effect of 'cat &gt;&gt;tmpppp &lt;&lt;&quot;EOF&quot;'"
date: 2015-09-03
forum: General Help
---

### Post by ruwan2 on 2015-09-03
Hi,
Originally, I type the command:

cat >>tmpppp <<"EOF"

it always at 
< 

waiting for input.

I have tried Ctrl+A Z, quit etc., it does not exit.
I only can use Ctrl+C to exit.

1. What use of the command:

cat >>tmpppp <<"EOF"

Is it to write the content to file tmpppp?
Why cannot I finish it?

2. How to finish that command at '<'?

3. "EOF" is the end of file character? Is it for a text file?

4. I just try an existing file tmpppp0. I enter two lines:
> ssssssssssssssssssssssssss
> ddddddddddddddddddddddddd

On termianl, it shows:

uj@MS-7696:~$ cat >>tmpppp0 <<"EOF"
> dsfakjsdfls
> ssssssssssssssssssssssssss
> ddddddddddddddddddddddddd
> bash: warning: here-document at line 38 delimited by end-of-file (wanted `EOF')

Ctrl+D makes the input terminating. But I don't understand the line number '38', even it only shows. '38' is much larger than the line present (less than 10).

Thanks,

---

### Post by Lars Noodén on 2015-09-03
The "cat <<EOF" part means that cat will willing to receive input until you enter a new line that contains only "EOF".  So to end the input, type "EOF" and press return.  

It is what is called a [here document](https://wpollock.com/ShScript/HereDoc.htm)

---

