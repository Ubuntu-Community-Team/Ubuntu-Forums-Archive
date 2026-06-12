---
title: "Creating and printing out random numbers"
date: 2015-07-14
forum: General Help
---

### Post by La_nce_Culp on 2015-07-14
I have used the following terminal commands to create random numbers and a directory. But I don't know how to print them out for pdf  files or paper distribution. Can any help me? Thanks!

[I]$ mkdir -p ~/.onetime
     $ dd if=/dev/random of=~/.onetime/to_foo.pad bs=1000 count=10000
 
 
   [/I]

---

### Post by Dreamer Fithp Apprentice on 2015-07-14
It may not matter to you, but just in case, it should be noted those are not random numbers, but pseudo-random numbers. In most applications it won't make much difference, but true random numbers can only be obtained from some external source, such as a hardware random number generator.

I don't know much about printing or editing pdfs but aren't you just producing a text file with your number in it with those commands? Can't you just right click and select print from your gui file manager? Or open it with a text editor and select a print option? Could be I don't understand the question.

---

### Post by nerdtron on 2015-07-14
> **La_nce_Culp said:**
> I have used the following terminal commands to create random numbers and a directory. But I don't know how to print them out for pdf  files or paper distribution. Can any help me? Thanks!

[I]$ mkdir -p ~/.onetime
     $ dd if=/dev/random of=~/.onetime/to_foo.pad bs=1000 count=10000
 
 
   [/I]

Are you sure about this? If I'm not mistaken, "/dev/random" does not contain random numbers but rather random 0s and 1s sequences. This results to a binary file. And dd is a dangerous command so be careful with it.

Anyway, if you just want a random number and output it to a file, you can use the built in $RANDOM variable in bash.
```
nerdtron:~$ echo $RANDOM
6433
nerdtron:~$ echo $RANDOM
24783
nerdtron:~$ echo $RANDOM
19401

```

If you want an automated way, here's an example to spit out 10 random numbers.
```
nerdtron:~$ for i in `seq 1 10`; do echo $RANDOM; done
18120
6463
3682
23015
21332
19755
32453
16166
1795
28562
```

---

### Post by tgalati4 on 2015-07-14
To see what PDF tools are on your system:

```
apropos PDF
```

Typically *groff* is used to take a text file and convert it to PDF.

Install the groff filters:

```
sudo apt-get install groff
```

Take nerdron's example and dump it to a file:

```
for i in `seq 1 10`; do echo $RANDOM; done > my10random_numbers.txt
```

Now perform the groff conversion:

```
groff -T pdf my10random_numbers.txt > my10random_numbers.pdf
```

There must be an easier or more elegant way of doing this.

---

### Post by La_nce_Culp on 2015-07-15
> **nerdtron said:**
> Are you sure about this? If I'm not mistaken, "/dev/random" does not contain random numbers but rather random 0s and 1s sequences. This results to a binary file. And dd is a dangerous command so be careful with it.

Anyway, if you just want a random number and output it to a file, you can use the built in $RANDOM variable in bash.
```
nerdtron:~$ echo $RANDOM
6433
nerdtron:~$ echo $RANDOM
24783
nerdtron:~$ echo $RANDOM
19401

```

If you want an automated way, here's an example to spit out 10 random numbers.
```
nerdtron:~$ for i in `seq 1 10`; do echo $RANDOM; done
18120


6463
3682
23015
21332
19755
32453
16166
1795
28562
```


Here is what I read about generating random numbers.

[COLOR=#333333][FONT=Verdana]"The random number generator gathers environmental noise from device drivers and other sources into an entropy pool. The generator also keeps an estimate of the number of bit of the noise in the entropy pool. From this entropy pool random numbers are created.[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]When read, the **/dev/random** device will only return random bytes within the estimated number of bits of noise in the entropy pool. **/dev/random** should be suitable for uses that need very high quality randomness such as one-time pad or key generation. When the entropy pool is empty, reads to **/dev/random** will block until additional environmental noise is gathered.


[/FONT][/COLOR]
  Anyway, your suggestion seems fine. But are the results from the commands you post truly random numbers? Are they created from the aforementioned entropy pool,or are they pseudo random numbers? 

Thanks

---

### Post by kurt18947 on 2015-07-15
Libreoffice calc has a random number function. I have no idea how truly random that function is.

---

### Post by Dreamer Fithp Apprentice on 2015-07-15
> **La_nce_Culp said:**
> But are the results from the commands you post truly random numbers?No. I repeat:> **Dreamer Fithp Apprentice said:**
> In most applications it won't  make much difference, but true random numbers can only be obtained from  some external source, such as a hardware random number  generator.No software only approach can produce truly random numbers. The inputs used to generate the entropy are not themselves strictly random. NO software, NO commands, NO programs. None. Zip. It is mathematically impossible. Close enough for most purposes, as I said. But if you want to be purist about it, you have to have truly random input, and if it's security you are concerned about, you shouldn't use a publicly available random number (such as published weather data or random numbers downloaded from a document on the internet). If it isn't a security issue, and you don't care if someone guesses what random number you've used, but you DO need a truly random number, there are lots of strings of random digits published on web sites. I think you could even use the digits of pi (but research that to make sure I'm right). Try startpage.com (like google minus the evil) to find them. If security IS an issue and you need a truly random number that nobody else has any way of improving their odds of guessing, then you need a locally generated random number. You could do it tediously with a 20 sided die by hand. Or measuring random objects with an absurdly accurate micrometer or balance and taking the least significant digit. Or maybe something similar with a locally made audio recording of noise.  If you just need a few hundred digits, the die is probably the most practical. Of course there MIGHT be bias in the die. I'm not sure how carefully 20-sided dice are made. 6-sided dice that are made pretty darned carefully are commercially available. If you wanted a binary string, you could count odds as 0 and evens as 1. If you wanted to generate a random decimal string with 6-sided dice, it could be done, but the exact method to do so, without introducing any digital bias, would bear thinking about. If you need so much random data that these methods aren't practical, and it needs to be not only truly random, but secure (non-published and not derived from guessable data), then there is no way around it - you need a hardware random number generator.  These can be add-in cards for a desktop or usb attached devices. Prices range quite a bit. I believe the least expensive are under a hundred USD. A purist may say they aren't quite as random as the more expensive ones based on radioactive decay but they are certainly a lot more random than any software-generated pseudo-random numbers.

You might want to search for articles on the subject. Finagle knows, randomness is hardly a neglected topic in mathematics or IT. You can read for days on it and hardly scratch the surface.

> **La_nce_Culp said:**
> Are they created from the aforementioned entropy pool,or are they pseudo random numbersThese are not alternatives. If you have any normal setup, the data in the entropy pool IS pseudo-random. ALL entropy created by software methods using things like mouse movement or keystroke timing as seeds is pseudo-random. Always. No exceptions. Maybe close enough, but strictly speaking, not random.

> **kurt18947 said:**
> Libreoffice calc has a random number function.  I have no idea how truly random that function is.Same story. It  probably uses the same backend tools already available in bash. Anyway,  it isn't random. Probably close enough, but not random.

---

### Post by La_nce_Culp on 2015-07-15
Very interesting. I didn't know that. Thanks, I will check that out, too.

---

### Post by La_nce_Culp on 2015-07-15
Nothing is ever simple--your remarks bring that adage to mind. In my case, security is a major issue.

Anyway, even before reading your post, I was contemplating buying a hardware based RNG. 



[https://grandst.com/marketplace/truerng](https://grandst.com/marketplace/truerng)
 
However, it will plug into a usb port and add pure randomness to the pool of "pseudo random numbers" generated by the dev/urandom function we have been discussing. Hence my questions about the way in which to access and print out the numbers from that particular pool remain pertinent to me.

If you have a chance, your opinion about the RNG I have listed will be appreciated. Thanks again.

---

### Post by steeldriver on 2015-07-15
I think we'd need to know more about (a) your application and (b) what format you want the output to be in

---

### Post by Dreamer Fithp Apprentice on 2015-07-15
> **La_nce_Culp said:**
> Nothing is ever simpleAin't it the truth?

> **La_nce_Culp said:**
>   I was contemplating buying a hardware based RNG.
[https://grandst.com/marketplace/truerng](https://grandst.com/marketplace/truerng)
However, it will plug into a usb port and add pure randomness to the pool of "pseudo random numbers" generated by the dev/urandom function we have been discussing. Hence my questions about the way in which to access and print out the numbers from that particular pool remain pertinent to me.Sounds like sound reasoning to me.

> **La_nce_Culp said:**
>  If you have a chance, your opinion about the RNG I have listed will be appreciated. Cool. Looks nice. Great price. It goes on my "toys to get" list. This looks a lot like the inexpensive RNGs I've read of in the past - might be the same one. With any of these things, if security is really important, you might want to investigate the product and company history. Who are these people? How long has this product been on the market? Has there been any testing by credible outsiders? I'm not deep enough on these issues yet to skeptically evaluate their technical claims, certainly not off the cuff. But it looks good. I suspect I'll buy one when I have 50 bucks to spare, which will probably happen sometime ere the protons all decay.

There is always the issue of trust. We know for example that the Nefarious Sucky Asses (Mods: The common name of Equus Assinus is not an obscenity, no matter what Sheldon Hackney may think. If anything, I'm insulting donkey-kind unfairly) put moles in some of the encryption standards committees to deliberately weaken the standards adopted, including the https standard. Recently there was another revelation, derived I believe, not from the gentleman in Russia, but from independent technical analysis, that another standard (something to do with website certs maybe, I forget) they influenced seems to have a built in back door. And if the parasites living on your taxes can do it, maybe so can the ones funded from China, Russia, Israel, la Cosa Nostra, or the Union Corse. It isn't at all inconceivable that there is hardware out there that someone has paid to have hidden functions in. Like for instance, just how much hidden space is their on modern hard drives that won't let the OS see what's going on inside, and is it used for anything other than remapping? RNGs, of course, are an obvious target.

Which is why I think in designing anything where security is important it is a good idea to consider "defense in depth" approaches if possible so as to minimize the consequences of failure of any one tactic.

 There is a heck of lot of interesting stuff to read on these kinds of topics at all levels.  If you have a general interest, I recommend checking out some of Cory Doctorow's speeches on Youtube. He isn't the best SF writer out there yet (but he might be by the time he's Niven's age) but he IS the most important, because he is a man with a mission, and clearly the successor to George Orwell. Like Heinlein, a lot of his message is targeted at the young with the clear intent of maximizing his long term effectiveness. Most of his books are available free, as in speech and as in beer, like GNU. Check out his website, and if you sympathize, give an ebook copy of Little Brother to every high school or middle school kid you know. See ya in the Gulag.

---

### Post by La_nce_Culp on 2015-07-15
> **nerdtron said:**
> Are you sure about this? If I'm not mistaken, "/dev/random" does not contain random numbers but rather random 0s and 1s sequences. This results to a binary file. And dd is a dangerous command so be careful with it.

Anyway, if you just want a random number and output it to a file, you can use the built in $RANDOM variable in bash.
```
nerdtron:~$ echo $RANDOM
6433
nerdtron:~$ echo $RANDOM
24783
nerdtron:~$ echo $RANDOM
19401

```

If you want an automated way, here's an example to spit out 10 random numbers.
```
nerdtron:~$ for i in `seq 1 10`; do echo $RANDOM; done
18120
6463
3682
23015
21332
19755
32453
16166
1795
28562
```

I feel compelled to ask again about these commands , which do seem to fit the bill. Are the numbers originating from dev/random? Are they generated by random computer activities, such as mouse movements. As I indicated in another post, I will endeavor to procure a hardware RNG that will add to the pool created by dev/random. 

Here is a possible choice:

[https://grandst.com/marketplace/truerng](https://grandst.com/marketplace/truerng)

Thanks again for your insightful advice.

---

### Post by La_nce_Culp on 2015-07-15
I think you might the following article interesting. I did. 
[http://imotp.sourceforge.net/noise.pdf](http://imotp.sourceforge.net/noise.pdf)

I will, indeed, check out Cory Doctorow's speeches.

---

### Post by nerdtron on 2015-07-15
Form the man pages:
> $RANDOM is an internal Bash [function]("http://www.tldp.org/LDP/abs/html/functions.html#FUNCTIONREF") (not a constant) that       returns a *pseudorandom          [[1]]("http://www.tldp.org/LDP/abs/html/randomvar.html#FTN.AEN5817")        integer in the range 0 - 32767. It should       [I]not* be used to generate an encryption       key. [/I]

It's called pseudorandom and not random, because being random (in computer terms) just doesn't exist at all. These numbers generated are considered random because they just meet a certain mathematical term to be considered random. And also, these generated number have a starting point, called a seed.
>  
[TABLE="class: FOOTNOTES, width: 100%"]
[TR]
[TD="width: 5%"][[1]]("http://www.tldp.org/LDP/abs/html/randomvar.html#AEN5817")[/TD]
[TD="width: 95%"]True "randomness," insofar as         it exists at all, can only be found in certain incompletely         understood natural phenomena, such as radioactive         decay. Computers only *simulate         randomness, and computer-generated sequences of         "random" numbers are therefore referred to as         [I]pseudorandom.*[/I][/TD]
[/TR]
[TR]
[TD="width: 5%"][[2]]("http://www.tldp.org/LDP/abs/html/randomvar.html#AEN5857")[/TD]
[TD="width: 95%"]The *seed of a           computer-generated pseudorandom number series           can be considered an identification label. For           example, think of the pseudorandom series with a           seed of [I]23* as *Series           #23*.[/I]
*A property of a pseurandom number series is the length of           the cycle before it starts repeating itself. A good pseurandom           generator will produce series with very long cycles.*[/TD]
[/TR]
[/TABLE]



from: [http://www.tldp.org/LDP/abs/html/randomvar.html](http://www.tldp.org/LDP/abs/html/randomvar.html)

---

### Post by La_nce_Culp on 2015-07-15
Very good info. Thanks.

I have one of Cory's speeches playing on Youtube--good stuff!!!!!!!!

---

### Post by Dreamer Fithp Apprentice on 2015-07-15
> **La_nce_Culp said:**
> I feel compelled to ask again about these commands , which do seem to fit the bill. Are the numbers originating from dev/random?I assumed so until your question stimulated me to read a bit on RANDOM. Apparently not. RANDOM is actually both a variable AND a function. The function takes a seed value and generates a pseudorandom number. Like any software generation of a pseudorandom number the process is purely deterministic and with the same seed value it will generate the same pseudorandom number again. The seed is the value of the variable RANDOM. You set it like any other variable, e.g.```
RANDOM=2
``` Then when you call the function with syntax that looks just like you're using a variable, e.g.```
echo $RANDOM
```first it uses the value of the variable RANDOM as a seed for the function RANDOM and  outputs a pseudorandom number in whatever range it is set for and of whatever quality it is set for, and then does SOMETHING to reset the seed. Experimentally, I have confirmed that it doesn't just use the last output, which would be terrible. Where the automatic new seed comes from, I haven't found out yet. But I've seen recommendations to manually seed RANDOM the first time you use it in a series of uses, which implies that the person writing that thinks the automatic seed is coming from some deterministic process that is part of RANDOM - like maybe hashing the previous output and keeping a record somewhere. Note that both range and quality (roughly, how good a simulation of randomness) are settable, not fixed as indicated in another answer. See man RANDOM. This may depend on the version. Mine is whatever is current in Trusty. But even at the highest quality setting (there are 5) , RANDOM is widely said to be NOT good enough for secure applications where you may have an opponent intelligently trying to exploit the difference between random and pseudorandom. Nelson posting at
[ http://stackoverflow.com/questions/1194882/generate-random-number]("http://stackoverflow.com/questions/1194882/generate-random-number")
goes further:

 " I wouldn't use it for a simulation (and certainly not for crypto), but it's probably adequate for basic scripting tasks.  If you're doing something that requires serious random numbers you  can  use /dev/random or /dev/urandom if they're available."

In other words he wouldn't even trust it to be sufficiently like random to not be defeated by the non-malicious, you might say, um, "random", effects of a physics simulation, in which the deviation from randomness might have consequences that accumulate, rather than cancel out. In other words, it's not very good at all.

That seems to reflect a widely shared opinion that RANDOM isn't anywhere near good enough, given your stated objectives.
Use RANDOM for when it just needs to look random to a casual observer, like in a game. A game not played for money, that is.
> **La_nce_Culp said:**
> Are they generated by random computer activities, such as mouse movements. Dunno, but I suspect not, or if so, not by enough of them. I think the idea of RANDOM is to be a source of LOW quality pseudorandom numbers that doesn't use up the content of /dev/random, which is, after all, a scarce resource normally.

If you buy the hardware RNG, I bet they'll have a manual, that will give you good tips on using it, maybe on their website somewhere. You might also want to read up on /dev/random. I believe it is configurable to some degree.

Thanks for the links. Interesting subject.

---

### Post by Dreamer Fithp Apprentice on 2015-07-15
> **La_nce_Culp said:**
> I have one of Cory's speeches playing on Youtube--good stuff!!!!!!!!Glad you like it. He's the latest inductee in my personal pantheon of heroes.  His website (named for one of his stories) is:
[URL="http://craphound.com/"]http://craphound.com/
[/URL] 
Note all the free e-book downloads. They are a little hard to find.
From the main page, you can click any of the covers on the right to go to a page about that book.
For example, the page for Little Brother:
[URL="http://craphound.com/category/littlebrother/#books"]http://craphound.com/category/littlebrother/#books
[/URL]
On the left half of that page will be a small button a little way down from the top, labeled "download e-book", which will take you to a page with links to download multiple formats, like this one:
[URL="http://craphound.com/littlebrother/download/"]http://craphound.com/littlebrother/download/ 
[/URL]But note there is interesting stuff further down the page below the buttons.

And on the page the button takes you to are links for the actual downloads, in many different formats. They are not all in one spot. Some are in a group near top left, others further down the page.  Give a copy to any bright kids you know.

---

### Post by La_nce_Culp on 2015-07-16
A few minutes ago,I just bought one of his books from Amazon. The title is Information Doesn't Want To Be Free: Laws for the Internet age. It's a Kindle book. I think I'm going to agree with most of what he has to say.

---

### Post by La_nce_Culp on 2015-07-16
Once again, thanks for you comprehenive look into this matter. It will help me move forward
with my various ecryption goals. I have some very practical reasons for the project, which
are off topic for this site.


I am still unsure about how to fully manipulate the dev/random pool. So I need to press forward on that
front. All suggestions will be appreciated.


I have ordered the TrueRNG, which will be used to fill the dev/random pool. On Amazon, the 
item is endorsed by none other than Dr. Dean Radin. He is a researcher whose opinion I hugely respect.
So I feel comfortable with my choce. 


You mighht be interested in some of Radin's books. Here's one:
Entangled Minds: Extrasensory Experiences in a Quantum RealityApr 25, 2006
by Dean Radin Ph.D.


And if you are interested in encryption, I suggest visiting the following site:


[http://users.telenet.be/d.rijmenants/index.htm](http://users.telenet.be/d.rijmenants/index.htm)


Rijmenants, the site's founder, remains convinced that no encryption method besides the 
one time pad code should be trusted. He still believes in the paper and pencil implimentation
of otp encryption. Some of his essays are most informative.


Additionally, Hack 5--which is one of my favorite Youtube stops--has an interesting
segement about the Red Bean one time pad code.


[https://www.youtube.com/watch?v=WkgumA5mHoI](https://www.youtube.com/watch?v=WkgumA5mHoI)


Unfortunately, most people don't use encryption and as Cory said in one of his presentations, you have to 
bring the rest of the world with you when it comes to encryption. Personally, I have a liking for RetroShare.

---

### Post by Dreamer Fithp Apprentice on 2016-01-21
Blows TrueRNG out of the water:
[http://www.bitbabbler.org/index.html](http://www.bitbabbler.org/index.html)
These guys appear to have really done it right.

---

