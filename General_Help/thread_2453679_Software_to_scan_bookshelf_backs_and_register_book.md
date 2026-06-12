---
title: "Software to scan bookshelf backs and register books?"
date: 2020-11-15
forum: General Help
---

### Post by Jenske on 2020-11-15
I have several hundred books on my bookshelves. I'd like to inventory these and input the books in my library software (Zotero).
I'd like to have the scanner software at least be able to distinguish backs from different books and OCR the text on the backs to separated entries. But it would also be nice if a recognized title could immediately be looked up in e.g. google of bol.com or whatever site that categorizes books.

Does any software exist that can achieve this?

---

### Post by TheFu on 2020-11-15
I don't know, but I'd bet there is software that would accept the ISBN number for any book and pull the relevant data back.  [https://isbnsearch.org/](https://isbnsearch.org/)
For example: [https://isbnsearch.org/isbn/0131411543](https://isbnsearch.org/isbn/0131411543) is a book I had nearby. The returned data is lacking, but still important.  I use Calibre to manage my published document horde. It prefers ebooks.

Scanning and doing OCR isn't a built-in capability, but you can use gscan2pdf to accomplish both.  Scanning anything but sheets of paper is a huge hassle.  The OCR accuracy is highly dependent on the font used by the creator.   What I do when scanning documents is to have the image on top and put the OCR'd text underneath each page.  I've seen only about 90% accuracy with the OCR tools. Rather than attempt to fix all the text under the image for each page, I'd just ensure any keywords that would be used for text searches would be spelled correctly.  After all, the point of the OCR'd text is for searching later. Nobody is going to try an read that OCR text - they will read the image.

The more I look into this, the less satisfying the total results have been.  Calibre did an ok job adding the book using the ISBN, but it didn't pull the back cover in, just the front.

---

### Post by Holger_Gehrke on 2020-11-15
Books printed after 1972 have an ISBN (International Standard Book Number). Once you have the ISBN Zotero should be able to get all the other data (title, author, date of publication ...) from the net (from worldcat, probably). For older Books the ISBN is usually given inside the book, newer books often have it as a bar code on the back. If you don't have a bar code reader lying around, zbarcam from the package zbar-tools can use a web-cam to read bar codes.

Holger

---

### Post by TheFu on 2020-11-15
I don't know, but I'd bet there is software that would accept the ISBN number for any book and pull the relevant data back.  [https://isbnsearch.org/](https://isbnsearch.org/)
For example: [https://isbnsearch.org/isbn/0131411543](https://isbnsearch.org/isbn/0131411543) is a book I had nearby. The returned data is lacking, but still important.  I use Calibre to manage my published document horde. It prefers ebooks.

Scanning and doing OCR isn't a built-in capability, but you can use gscan2pdf to accomplish both.  Scanning anything but sheets of paper is a huge hassle.  The OCR accuracy is highly dependent on the font used by the creator.   What I do when scanning documents is to have the image on top and put the OCR'd text underneath each page.  I've seen only about 90% accuracy with the OCR tools. Rather than attempt to fix all the text under the image for each page, I'd just ensure any keywords that would be used for text searches would be spelled correctly.  After all, the point of the OCR'd text is for searching later. Nobody is going to try an read that OCR text - they will read the image.

The more I look into this, the less satisfying the total results have been.  Calibre did an ok job adding the book using the ISBN, but it didn't pull the back cover in, just the front. See the attachment.

---

### Post by Jenske on 2020-11-16
As not all books have an ISBN-number and as I have quite a lot of older books, using the ISBN-number would only resolve part of my problem.
I should maybe have mentioned that a lot of my books are in Dutch. And I do know that a lot of them are in reference lists of other researchers, but a lot of those do not have an ISBN-number.

So I was wondering whether there exists a system that can recognize the back of books, like face recognition. Other example: if I photograph a CD cover and enter it as a google-search image, Google easily finds the corresponding information on the music and even the song titles on that CD.

It would already be a great help if a photograph of the back of my books on a shelf could be divided into seperate books and, using OCR, would give me the words or titles that are on the back of the books.

---

### Post by dragonfly41 on 2020-11-16
My thought is that you could use some machine learning service (of book images) where book images are categorised into buckets.
You would need to "train" the algorithm with examples.

---

### Post by Impavidus on 2020-11-16
> **Holger_Gehrke said:**
> ... newer books often have it as a bar code on the back.

> **Jenske said:**
> ... a system that can recognize the back of books, like face recognition.

I guess you're talking about different backs of books. There's the rear face, often with a summary of the book's contents or something about the author, and there's the narrow side, visible when the book is on a shelf, usually with title, author and publisher, in no particular order and in a variety of orientations and (sometimes very artistic) fonts. I think that will be hard for OCR. If you had 20000 books, look further, but with only a few 100 you should be able to do it manually in a few hours. It's boring, but doable.

---

