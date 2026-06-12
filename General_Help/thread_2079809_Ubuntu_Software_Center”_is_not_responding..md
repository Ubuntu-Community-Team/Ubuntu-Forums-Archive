---
title: "Ubuntu Software Center” is not responding."
date: 2012-11-02
forum: General Help
---

### Post by workaround on 2012-11-02
I get this error message: “The window “Ubuntu Software Center” is not responding.” Force to quit!?
Any way to deal with that?
Thanks.:confused:

---

### Post by evilsoup on 2012-11-02
Yeah, it happens sometimes, the Software Centre is horribly buggy. If you just open it again, it should work (until it breaks again at random).

If you're using 12.10, then you can mostly use the dash to replace the Software Centre, search in the applications lens and right-click on the suggestions.

Some people prefer using Synaptic. And, of course, there's always the command line.

---

### Post by workaround on 2012-11-02
I cannot even get to the command line!?

---

### Post by Paari on 2012-11-02
Press "Ctrl + Alt + T" to open terminal...

Enter the code below to get Synaptic Package Manager. You can use it as an alternative for Ubuntu Software center...

```

sudo apt-get install synaptic

```

---

### Post by workaround on 2012-11-02
this sudo installed something but it did not fix the problem. The lib of software does not come up at all except to give me an error.

---

### Post by lisati on 2012-11-02
> **workaround said:**
> this sudo installed something but it did not fix the problem. The lib of software does not come up at all except to give me an error.

What was the error you saw?

(As an aside, it won't have been "sudo" that did the work, but "apt-get". A common use of sudo in the suggestions made in this forum is to temporarily give your "admin" user the extra permissions necessary to do "admin" stuff.)

---

### Post by workaround on 2012-11-02
When I referred to "sudo" I meant the entire line of  sudo apt-get install synapticIn regard to that, the error is the same, it just does not load the software center. When I try to search thru the Dash Home for like PHP it cannot find anything.
So, the only way to install PHP is downloading the software and then installing it from the command line, correct?:popcorn:

---

### Post by evilsoup on 2012-11-02
That command line installed synaptic, which is similar to the software centre except less pretty, but more stable. Some people prefer using that to install software.

If you click [here](apt://php5), the software centre should open up, and you should be able to install PHP 5. Alternatively, search for PHP in the software centre or Synaptic (you'll have to click 'show *x* technicla items' for it to show up in the software centre; look for the package titles php5); alternatively alternatively, you can install it from the command line with

```
sudo apt-get install php5
```

---

