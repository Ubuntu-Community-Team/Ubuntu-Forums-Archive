---
title: "Refer to a file path in command line?"
date: 2019-06-08
forum: General Help
---

### Post by PDA1 on 2019-06-08
I'm trying to use PDFTK to combine several pdfs by referring to the pdf location....but can't figure it out.  I want to be able to work in any folder, have pdftk "go get" the pdfs (no matter what folder they're located in), combine them and then send the output to the folder I'm working in.

I can combine (cat) the file quite easily using pdftk when they're in the same folder but referring to them in other assorted folders doesn't work.

Command line always says there's some error such as it can't find the file, etc.  I suppose I'm using the incorrect format for referring to a file.

Example- 

2 files needed to be combined (notice there are spaces in the folders and file names) Notice this is from the command line-
 
Paul@Paul:~/My Documents/AAA- My Method/Supplement/0- Disclaimer and Credits$
 
Disclaimer for 1993.pdf  
 
Paul@Paul:~/My Documents/AAA- My Method/Supplement/1- Covers for The Book$  
 
The Cover for 1993.pdf   
  


Here's what I'm come up with so far (this is all pasted into command line)

```
pdftk \
 /My Documents/AAA- My Method/Supplement/1- Covers for The Book\The Cover for 1993.pdf \
 /My Documents/AAA- My Method/Supplement/0- Disclaimer and Credits\Disclaimer for 1993.pdf \
 cat \
 /My Documents/AAA- My Method/Supplement/1- Covers for The Book\The Cover for 1993.pdf \
 /My Documents/AAA- My Method/Supplement/0- Disclaimer and Credits\Disclaimer for 1993.pdf \
 
 outputFinalFile.pdf
  
```

Can you solve this for me?

Thank you,

Paul

---

### Post by TheFu on 2019-06-08
You need to understand the different between *relative paths* and *absolute paths*.

Begin with your HOME directory.  Maybe not.  userids should be all lowercase - there are reasons for that. This also would make your HOME directory /home/paul/ if defaults are used. That's the *absolute path* to your HOME.
**env |grep HOME** will show this.
Same for **echo $HOME**.
**~/ **for any userid points to the current HOME directory.   Most prompts on Unix show the HOME as **~**.
Say there is another userid on the system, thefu, then the HOME directory for that userid is **~thefu**.

If you use tab completion, you can check the correct path for any file.  If you aren't using tab completion, Unix must totally suck for you.  Stop whatever you are doing and learn to use tab completely.  Please, please, please.

So, we've learned that
$HOME == ~/ == /home/paul
They are all the same for a userid named "paul" if the defaults are used.

So if we look at the prompt above .... 
```
Paul@Paul:~/My Documents/AAA- My Method/Supplement/0- Disclaimer and Credits$
```
That is userid@hostname:$CWD
So, 
```
userid = Paul
hostname = Paul
CWD = "~/My Documents/AAA- My Method/Supplement/0- Disclaimer and Credits"

```
Notice the ~/My .....    that ~/ at the beginning is critical. Absolutely critical.

BTW, hostnames should be all lowercase too.  Reasons.

So, CWD = Current Working Directory. That is also the PWD = Present Working Directory.  There is a command, **pwd** - it will show the PWD/CWD, but the prompt always shows that.  The $CWD and $PWD variables sometimes contains the **pwd**.
```
echo $CWD
echo $PWD

```
BTW, life is easier if you don't have spaces in directories or file names.  Scripting when there are spaces in file paths means taking extra care on quoting all variables and any paths. Without quotes, the scripting will fail.

And please don't use odd fonts posting.

---

### Post by PDA1 on 2019-06-08
So, then how should the code appear given my examples?

---

### Post by coffeecat on 2019-06-08
@PDA1, I've restored the default font properties in your post. Please use non-default font formatting only for highlighting purposes. Also, I've never seen so much interfering BBCode inside BBCode code tags before - which I have removed. Text such as yours inside code tags gets mal-formatted if you use other BBCode inside the code tags.

---

### Post by PDA1 on 2019-06-08
Thanks, I guess.  I couldn't figure out how to delete the 2nd post.

---

### Post by spjackson on 2019-06-08
> **PDA1 said:**
> 
```
pdftk \
 /My Documents/AAA- My Method/Supplement/1- Covers for The Book\The Cover for 1993.pdf \
 /My Documents/AAA- My Method/Supplement/0- Disclaimer and Credits\Disclaimer for 1993.pdf \
 cat \
 /My Documents/AAA- My Method/Supplement/1- Covers for The Book\The Cover for 1993.pdf \
 /My Documents/AAA- My Method/Supplement/0- Disclaimer and Credits\Disclaimer for 1993.pdf \
 
 outputFinalFile.pdf
  
```

Apart from the ~ pointed out be TheFu, you seem to have 2 more issues: 1. some backslashes that should be forward slashes, 2. spaces in filenames. So...
```
pdftk \
 cat \
  ~/"My Documents/AAA- My Method/Supplement/1- Covers for The Book/The Cover for 1993.pdf" \
  ~/"My Documents/AAA- My Method/Supplement/0- Disclaimer and Credits/Disclaimer for 1993.pdf" \
  ~/"My Documents/AAA- My Method/Supplement/1- Covers for The Book/The Cover for 1993.pdf" \
  ~/"My Documents/AAA- My Method/Supplement/0- Disclaimer and Credits/Disclaimer for 1993.pdf" \
  outputFinalFile.pdf
  
```

---

### Post by PDA1 on 2019-06-08
Figured it out. 

Thanks.

---

