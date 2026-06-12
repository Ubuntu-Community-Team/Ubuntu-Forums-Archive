---
title: "Edit GEdit's Snippets"
date: 2008-04-17
forum: General Help
---

### Post by krU6)#43 on 2008-04-17
Hi all

I've just started using GEdit for my web dev work. For example coding in PHP.

The snippets are great because I've been using TextMate for the last year.

However, I don't like all of the snippets and have gone to the snippet manager and edited quit a few in there. After making my changes I close the snippet manager.

After reopening GEdit all my snippet modifications are lost!

Is someone able to tell me how to save the edited snippets so they are persistent, or is this a bug?

Many thanks

---

### Post by sam hassell on 2008-04-17
hi,

On my (hardy) installation it works as expected.

i code php - i cant use the php snippets unless i have a php file open - would that be your problem?

i cant test in gutsy unfortunately.

HTH.

---

### Post by krU6)#43 on 2008-04-17
Hello

Thanks for your reply.

I'm coding in PHP, GEdit is setup for PHP and the snippets work.

The problem is if I edit the PHP snippets in the snippet manager, my changes are lost if I reopen gedit.

Would you mind editing one of your PHP snippets, add in an extra space or something. Close down all instances of GEdit, then open GEdit. Go back in to snippet manager and check the snippet you edited. Are your changes still there? Mine aren't.

Kind regards

Gabriel Dragffy

---

### Post by sam hassell on 2008-04-17
Yeah I can confirm that it works under hardy.

I just had a look around and the snippets are stored in ~/.gnome2/gedit/snippets as XML files.

The file with my custom PHP snippet is called php.xml in that directory.

The contents of it are:

> 
<?xml version='1.0' encoding='utf-8'?>
<snippets language="php">
  <snippet>
    <text><![CDATA[$sql = "${1:select query}";
$res = mysql_query($sql);
while ($row = mysql_fetch_array($res)) {
  ${2:# code...}
}]]></text>
    <tag>select</tag>
    <description>select</description>
  </snippet>
</snippets>


Do you have this file? Maybe check the permissions on the snippets directory, it should have read for everyone.

I cant find any bug reports about this for gutsy.

---

### Post by krU6)#43 on 2008-04-17
Hi 

Thanks for your reply.

I do have that file. I deleted it, then edit a PHP snippet again. The file was recreated, so the permissions would seem to be OK. However, the file only contains:
```
<?xml version='1.0' encoding='utf-8'?>
<snippets language="php" />
```

No matter how I edit the snippet.

Please, would you be kind enough to describe the exact steps you took so that your edits were saved?

Many thanks

Gabriel Dragffy

---

### Post by sam hassell on 2008-04-17
sure - although i did nothing explicit to save the snippet.

1. Applications -> Accessories -> Text Editor
2. Open temp.php (located in ~)
3. Tools -> Manage Snippets 
    (alternatively Edit -> Prefs -> Plugins -> Snippets -> Configure Plugin)
4. Select PHP from the list on the left
5. Click the Create New Snippet button at bottom left
6. Enter the code in the Edit textarea
7. Enter a tab trigger
8. Click close
9. Snippet now works.


I tested it using both methods of getting the manage snippets page up.

---

### Post by krU6)#43 on 2008-04-17
Ah thanks very much.

I haven't been trying to create a new snippet. I've been editing the ones that are in the plugin. Would you mind trying to edit an existing PHP snippet (one that you didn't create) and see if it is saved, even after restarting GEdit.

Many thanks

---

### Post by sam hassell on 2008-04-17
aahh ok,

the snippets that are already there are at /usr/share/gedit-2/plugins/snippets and by default you will not have write permission to that folder.

try:
> 
sudo chmod a+w /usr/share/gedit-2/plugins/snippets/*


or something similar.

---

### Post by krU6)#43 on 2008-04-17
Great! Thanks very much. I got it working by doing:
```
cp /usr/share/gedit-2/plugins/snippets/* ~/.gnome2/gedit/snippets
```

This way they can be overridden without leaving the /usr mount open to being filled up by anyone.

Thanks again for your help.

Kind regards

---

### Post by sam hassell on 2008-04-17
Thanks for discovering it! 

I filed a bug report at [https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/218998](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/218998) so we can get this fixed permanently. 

If you could confirm the bug and add any of your own comments that would help.

---

