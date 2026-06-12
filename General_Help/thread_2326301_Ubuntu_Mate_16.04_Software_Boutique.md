---
title: "Ubuntu Mate 16.04 Software Boutique"
date: 2016-05-30
forum: General Help
---

### Post by poorguy on 2016-05-30
Hey All,

Question about the Software Boutique in Ubuntu Mate 16.04. I would like to download xsensors but don't find it listed in the Software Boutique. Is it safe to download and install it using the terminal by sudo apt-get install xsesnors

Thanks

---

### Post by Impavidus on 2016-05-30
It doesn't matter whether you use software boutique, synaptic, apt-get or any other incarnation of the package manager. They all use the same repositories and check the same dependencies. If you know the name of the package you need, nothing is easier than installing it from the command line.

---

### Post by poorguy on 2016-05-30
Hey Impavidus,

Wasn't sure since it was 16.04.

Thanks.


				 				 					 						 	[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1417721")

---

### Post by howefield on 2016-05-30
> **poorguy said:**
> Is it safe to download and install it using the terminal by sudo apt-get install xsesnors

Not to muddy the waters I hope but.. :)

In 16.04 you have the cool *apt install* as well as *apt-get install*.

```
sudo apt install xsensors
```

would be the same as 

```
sudo apt-get install xsensors
```

Well, it isn't quite the same, you get a nice progress bar when using *apt*.

---

### Post by poorguy on 2016-05-30
> **howefield said:**
> Not to muddy the waters I hope but.. :)

In 16.04 you have the cool *apt install* as well as *apt-get install*.

```
sudo apt install xsensors
```

would be the same as 

```
sudo apt-get install xsensors
```

Well, it isn't quite the same, you get a nice progress bar when using *apt*.

Hey howefield,

The whole reason for my question is what you posted in the boxes. I kept seeing a difference in the commands. And yes it is a nice progress bar.

Thanks

---

