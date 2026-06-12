---
title: "[SOLVED] Huffman coding tool available?"
date: 2008-05-18
forum: General Help
---

### Post by Rytron on 2008-05-18
Hi,
Are any of you familiar with Huffman coding?
In college when exercises on this need to be done it takes a load of writing. Is there a tool online or better yet in Ubuntu that allows for working them out? I know how to solve them but having a tool would be a great help.
Thanks.

---

### Post by sdennie on 2008-05-18
Something like this: [http://www.codeproject.com/KB/recipes/HandyHuffmanCoding.aspx](http://www.codeproject.com/KB/recipes/HandyHuffmanCoding.aspx) might be useful for you.  Also, from the bzip2 man page:

```

bzip2  compresses  files  using  the Burrows-Wheeler block 
sorting text compression algorithm, and Huffman coding

```

I'm not sure if that's useful but, you could look at a hex dump of what bzip2 would do to a file with:

```

bzip2 -c some_file | od -x

```

---

### Post by Rytron on 2008-05-19
> **vor said:**
> Something like this: [http://www.codeproject.com/KB/recipes/HandyHuffmanCoding.aspx](http://www.codeproject.com/KB/recipes/HandyHuffmanCoding.aspx) might be useful for you.  Also, from the bzip2 man page:

```

bzip2  compresses  files  using  the Burrows-Wheeler block 
sorting text compression algorithm, and Huffman coding

```

I'm not sure if that's useful but, you could look at a hex dump of what bzip2 would do to a file with:

```

bzip2 -c some_file | od -x

```


Hi,
Sorry but I should have elaborated on what I meant. Please check out Question 5 on this past [exam paper]("http://exams.cit.ie/PastExams/Mathematics%20&%20Computing/COMP2/2007%20Autumn/Internet%20Studies%20&%20Web%20Design.pdf"). I require a tool to organise the letters around instead of having to rewrite the workings. Cheers.

---

### Post by Rytron on 2008-06-09
I'll stay with pen and paper for drawing up the huffman diagrams.

---

