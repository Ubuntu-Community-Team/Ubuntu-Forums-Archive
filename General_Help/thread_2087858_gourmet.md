---
title: "gourmet"
date: 2012-11-24
forum: General Help
---

### Post by tombull50 on 2012-11-24
I installed gourmet and added a recipe, the program looks pretty cool. I closed and reopened gourmet and now it will not open. I removed and re-installed gourmet but still will not open and I get this error message:

 (gourmet:9809): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
sqlite:////home/tommy/.gourmet/recipes.db
RECREATE USDA WEIGHTS TABLE
Attempting to alter  usda_weights <bound method NutritionDataPlugin.setup_usda_weights_table of <nutritional_information.data_plugin.NutritionDataPlugin instance at 0x3c052d8>> {} ['ndbno', 'seq', 'amount', 'unit', 'gramwt', 'ndata', 'stdev']
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
OperationalError: (OperationalError) there is already another table or index with this name: usda_weights_temp 'ALTER TABLE usda_weights RENAME TO usda_weights_temp' ()
Problem updating plugin <nutritional_information.data_plugin.NutritionDataPlugin instance at 0x3c052d8> nutritondata
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

### Post by ibjsb4 on 2012-11-24
Gourmet appears to be a little buggy.

[http://ubuntuforums.org/showthread.php?t=2062259](http://ubuntuforums.org/showthread.php?t=2062259)

[http://ubuntuforums.org/showthread.php?t=2039749](http://ubuntuforums.org/showthread.php?t=2039749)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=gourmet&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=gourmet&as_qdr=all&sa=Google+Search&lang=en)

---

