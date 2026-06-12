---
title: "Gourmet Recipe Manager Crashes"
date: 2012-12-17
forum: General Help
---

### Post by coreybell on 2012-12-17
I have been having a problem with my gourmet recipe manager in ubuntu 12.10, it was working fine up until a week ago, when it would not open at all, the program will start, show the image of the gourmet manager, then it will just crash with out even opening. I really like this program and would like to know if there is a way to fix it?

---

### Post by Impavidus on 2012-12-18
I don't know that program, but can you start it from  a terminal? It may give you a useful error message before crashing. Also, some programs produce a log file somewhere or leave a message in a system log.

---

### Post by ibjsb4 on 2012-12-18
> **Impavidus said:**
> I don't know that program, but can you start it from  a terminal? It may give you a useful error message before crashing

In case you don't know how to do that.

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
gourmet
```

---

### Post by coreybell on 2012-12-18
Thanks for the information, I think I found the problem, but I do not know how to fix it, I have posted it below, is there any information you can give me to help I have highlighted it below, along with all the information from the terminal: 

sqlite:////home/corey/.gourmet/recipes.db
RECREATE USDA WEIGHTS TABLE
Attempting to alter  usda_weights <bound method NutritionDataPlugin.setup_usda_weights_table of <nutritional_information.data_plugin.NutritionDataPlugin instance at 0xabd4e6c>> {} ['ndbno', 'seq', 'amount', 'unit', 'gramwt', 'ndata', 'stdev']
Traceback (most recent call last):
  File "/usr/share/gourmet/gourmet/backends/db.py", line 931, in alter_table
    self.db.execute('ALTER TABLE %(t)s RENAME TO %(t)s_temp'%{'t':table_name})
  File "/usr/lib/python2.7/dist-packages/sqlalchemy/engine/base.py", line 2447, in execute
    return connection.execute(statement, *multiparams, **params)
  File "/usr/lib/python2.7/dist-packages/sqlalchemy/engine/base.py", line 1449, in execute
    params)
  File "/usr/lib/python2.7/dist-packages/sqlalchemy/engine/base.py", line 1628, in _execute_text
    statement, parameters
  File "/usr/lib/python2.7/dist-packages/sqlalchemy/engine/base.py", line 1698, in _execute_context
    context)
  File "/usr/lib/python2.7/dist-packages/sqlalchemy/engine/base.py", line 1691, in _execute_context
    context)
  File "/usr/lib/python2.7/dist-packages/sqlalchemy/engine/default.py", line 331, in do_execute
    cursor.execute(statement, parameters)
[B]OperationalError: (OperationalError) there is already another table or index with this name: usda_weights_temp 'ALTER TABLE usda_weights RENAME TO usda_weights_temp' ()
Problem updating plugin <nutritional_information.data_plugin.NutritionDataPlugin instance at 0xabd4e6c> nutritondata[/B]
Traceback (most recent call last):
  File "/usr/bin/gourmet", line 35, in <module>
    gourmet.GourmetRecipeManager.startGUI()
  File "/usr/share/gourmet/gourmet/GourmetRecipeManager.py", line 715, in startGUI
    r=RecGui(splash_label=splash.label)
  File "/usr/share/gourmet/gourmet/GourmetRecipeManager.py", line 918, in __init__
    GourmetApplication.__init__(self, splash_label=splash_label)
  File "/usr/share/gourmet/gourmet/GourmetRecipeManager.py", line 114, in __init__
    self.setup_recipes() # Setup recipe database
  File "/usr/share/gourmet/gourmet/GourmetRecipeManager.py", line 204, in setup_recipes
    self.rd = recipeManager.default_rec_manager()
  File "/usr/share/gourmet/gourmet/recipeManager.py", line 131, in default_rec_manager
    return get_recipe_manager(**dbargs)
  File "/usr/share/gourmet/gourmet/recipeManager.py", line 126, in get_recipe_manager
    return RecipeManager(**args)
  File "/usr/share/gourmet/gourmet/backends/db.py", line 1769, in __init__
    RecData.__init__(self,*args,**kwargs)
  File "/usr/share/gourmet/gourmet/backends/db.py", line 165, in __init__
    self.update_version_info(gourmet.version.version)
  File "/usr/share/gourmet/gourmet/backends/db.py", line 598, in update_version_info
    (current_super,current_major,current_minor)
  File "/usr/share/gourmet/gourmet/backends/db.py", line 640, in update_plugin_version
    plugin_current = plugin.version,
  File "/usr/share/gourmet/gourmet/plugins/nutritional_information/data_plugin.py", line 68, in update_version
    [name for lname,name,typ in parser_data.WEIGHT_FIELDS])
  File "/usr/share/gourmet/gourmet/backends/db.py", line 944, in alter_table
    del self.metadata.tables[table_name]
  File "/usr/lib/python2.7/dist-packages/sqlalchemy/util/_collections.py", line 38, in _immutable
    raise TypeError("%s object is immutable" % self.__class__.__name__)
TypeError: immutabledict object is immutable

---

### Post by ibjsb4 on 2012-12-18
Update coreybell:

Just to let you know I am working on a solution to this and have a question.

Did you backup your recipe collection with the "export all recipes" option?

If not, that will be ok, I can create a backup from existing files.  Just need to know.

---

### Post by coreybell on 2012-12-18
No I did not sorry, if I can get it fixed I will start doing that, thanks for your help.

---

### Post by tgalati4 on 2012-12-19
Reminds me of this cartoon:

[http://xkcd.com/327/](http://xkcd.com/327/)

---

### Post by ibjsb4 on 2012-12-19
Hi there  :)

```
cp ~/.gourmet/recipes.db ~/recipes.db.backup && mv .gourmet .gourmet.original && sudo apt-get purge -y gourmet && sudo apt-get install gourmet && mv ~/.gourmet.original ~/.gourmet && gourmet
```

Copy and paste this code to terminal and enter. 

You will be asked for your password.  When entering your password in terminal you will not have any visual confirmation, just type it in and enter.

There will be a new file in your home directory called "recipes.db.backup".  This file is a built in safely for me and can be deleted if Gourmet Recipe Manager now works for you.

---

### Post by coreybell on 2012-12-19
That didn't work, it did the same thing the program started and before it opened it crashed.

---

### Post by ibjsb4 on 2012-12-20
In terminal:
```
rm -r ~/.gourmet && sudo apt-get remove --purge -y gourmet && sudo apt-get autoremove -y && sudo apt-get install gourmet -y && gourmet
```

You should now have Gourmet without your recipes.  If Gourmet is still not working, stop here and post back.

If Gourmet is working then please shut down the Gourmet program and in terminal enter:
```
rm ~/.gourmet/recipes.db && cp ~/recipes.db.backup ~/.gourmet/recipes.db
```

And try the program again.

---

### Post by coreybell on 2012-12-20
I tried it and it opened the gourmet program, and it seems to have worked, I will try it for a couple of days, and see what happens, I will close the thread for now. Thanks a lot, you have been a big help. By the way how are you with Evolution mail client?

---

### Post by ibjsb4 on 2012-12-20
Good deal  :)

Yes, go ahead and run it for a few days and if still happy with it:

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Don't forget to make a backup.

I do not run Evolution, so better to find some help from the experience users.  I would suggest starting a new thread on it.  Also, you may want to take a look through here.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Evolution+mail+client&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Evolution+mail+client&as_qdr=all&sa=Google+Search&lang=en)

And welcome to the forum  :D

---

### Post by coreybell on 2012-12-21
Thanks again, I really appreciate it.

---

### Post by Mark_in_Hollywood on 2013-01-16
I have 1001 recipes. Is that beyond GRM's limits? GRM will not export "All recipes" in any format. Selecting the Export function does nothing. GRM stays on screen but that's all. I could edit any recipe, export a recipe (HTML, TEXT, PDF) but that's all. And search still doesn't work. It's been a year or so with that. So I took to exporting all the recipes in .txt so that I could search for ingredients, recipe names, etc., but not even that's gone.

I have re-installed by GRM using the command line above for the original poster.

---

### Post by jpvrla on 2013-05-24
I think this thread needs to be reopened.   Last week I added some recipes to the "gourmet recipe manager" application.   Today I'm getting the same exact "TypeError: immutabledict object is immutable" error as listed earlier.   I continue to get the same error after removing and re-installing.  It seems to be python related.

It loads OK on a different disk with an older kernel but it only has half the recipes.  I am going to try copying the current GRM db to the older disk and see if it will run good on the drive with the older Ubuntu version.

Anyone else having this experience or a fix?

Ubuntu 12.04 (precise) Kernel 3.2.0-44, GCC 4.6(x86_64-linux-gnu)   Intel i5 650@3.20GHz

---

### Post by jpvrla on 2013-06-11
> **jpvrla said:**
> I think this thread needs to be reopened.   Last week I added some recipes to the "gourmet recipe manager" application.   Today I'm getting the same exact "TypeError: immutabledict object is immutable" error as listed earlier.   I continue to get the same error after removing and re-installing.  It seems to be python related.

It loads OK on a different disk with an older kernel but it only has half the recipes.  I am going to try copying the current GRM db to the older disk and see if it will run good on the drive with the older Ubuntu version.

Anyone else having this experience or a fix?

Ubuntu 12.04 (precise) Kernel 3.2.0-44, GCC 4.6(x86_64-linux-gnu)   Intel i5 650@3.20GHz.

Received private message referring me to this link [https://github.com/thinkle/gourmet#readme](https://github.com/thinkle/gourmet#readme).   Afterward I saved db, uninstalled recipe mgr, reinstalled recipe mgr, loaded saved db.  A few of the recipes had to be rebuilt since the data was jumbled (things were not where they should be).  I am not sure why.

---

### Post by Mark_in_Hollywood on 2013-06-11
GRM, as originally built (coded?) has a limit of 1000 recipes, I believe. The creator of it, Tom Hinkle, seemed surprised when I posted that I had 1008 recipes. I believe GRM is being re-worked to accomodate that. I had entered some recipes via the URL line. The recipes were Chinese, although in English language. But the ingredients preceeded the quantities and stuff like that. I never bothered fixing it. That is when GRM broke. I could not search for recipes and the db was a mess. It put blank spaces or unacceptable characters (such as ; or . ) into the fields. I eventually manually fixed about 30 recipes. For some reason, every update of Ubuntu has code that snarls GRM. Something to do with the Python stuff if I recall correctly. It will never be fixed in that sense. Every time you upgrade, it would be well to do two backups, and export all the recipes as a text file. I do. I have learned this the hardest way possible.

---

### Post by jpvrla on 2013-07-01
Closed, had to repaire about 10 of 70 recipes.

---

