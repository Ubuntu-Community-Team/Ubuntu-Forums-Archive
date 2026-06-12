---
title: "Gnome Nautilus file manager folder copy – overwrite problem"
date: 2006-10-25
forum: General Help
---

### Post by davescafe on 2006-10-25
I am having a folder copying problem in Nautilus that is causing me a lot of concern. 

I have a folder containing about five hundred documents that I need to use at work and at home. Every day, I add to this folder, both at work and at home. I have tried to synch-up the folders by copying one over the other. I expect to have a single folder when I am done, that contains all of the documents from work and all of the documents from home, combined. This is what happens if I copy using the terminal, but not within Nautilus. When I use the Nautilus file manager, the combined folder is only a fraction of the size it should be. When I try to copy the folder from work, over the identically-named folder from home, a dialog pops-up informing me that some of the files have the same name, and asking if I want to overwrite them. I say “yes to all”. But instead of the result being a single folder with 500+ documents, I end up with a folder containing only 60 documents. It appears all the documents that had the same titles in both the work and the home folders have been deleted, rather than overwritten, as expected.

It is a rather simple problem to demonstrate, but I confess it is a bit hard for me to explain in words. But it is causing me a lot of concern, because I don’t feel I can trust Ubuntu for even simple file management tasks.

Does anyone have any explanation or information as to why this is happening? I am already aware of how to do this at a terminal, but I would rather not.

Here’s an example:

Folder begins at home. It is named “Storage”. It has 500 documents inside it. Each document is named by the date and time it was created, so each document title is unique.

I copy “Storage” on a USB drive and take it to work. 

At work, I add 10 new documents to “Storage” at work. During this time, I also add another 15 documents the copy of “Storage” I have at home. Each of the new documents I add is named for the date and time I create them, so I am not worried that they will copy over each other.

After a month or so, I want to synch-up my “Storage” folders from work and home.

I copy “Storage” from work, on a USB drive and take it back home.

At home, I copy the “Storage” from work (on the USB drive), over the top of the “Storage” folder that is on my home computer. I choose to overwrite all the documents with the same titles.
Expectation: a single folder named “Storage” containing 525 documents.

Actual result: a single folder named “Storage” containing something like 60 documents.

---

