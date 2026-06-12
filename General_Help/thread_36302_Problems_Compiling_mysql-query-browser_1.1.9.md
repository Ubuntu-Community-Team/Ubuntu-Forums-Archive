---
title: "Problems Compiling mysql-query-browser 1.1.9"
date: 2005-05-22
forum: General Help
---

### Post by 76thParadox on 2005-05-22
I have tried to compile version 1.1.9 of the mysql-query-browser on my Ubuntu (5.04 AMD64) distribution of Linux. The compilation has failed. I was previously able to build version 1.1.7 without any problems. (Although the previous version seg faulted when trying to connect to a database, that is the reason I am trying to build this newer version.)

The compilation fails when trying to run make against the mysql-query-browser component. The common-gui components seem to build okay. The output from the make command follows below. Any advice on how to resolve this problem would me most appreciated.

[email]bjl@hephaistos:~/mysql-query-browser-1.1.9.tar.gz[/email]_FILES/mysql-query-browser-1.1.9/mysql-query-browser$ make
Making all in library
make[1]: Entering directory `/home/bjl/mysql-query-browser-1.1.9.tar.gz_FILES/mysql-query-browser-1.1.9/mysql-query-browser/library'
Making all in source
make[2]: Entering directory `/home/bjl/mysql-query-browser-1.1.9.tar.gz_FILES/mysql-query-browser-1.1.9/mysql-query-browser/library/source'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/bjl/mysql-query-browser-1.1.9.tar.gz_FILES/mysql-query-browser-1.1.9/mysql-query-browser/library/source'
Making all in tests
make[2]: Entering directory `/home/bjl/mysql-query-browser-1.1.9.tar.gz_FILES/mysql-query-browser-1.1.9/mysql-query-browser/library/tests'
Making all in test_query_analyze
make[3]: Entering directory `/home/bjl/mysql-query-browser-1.1.9.tar.gz_FILES/mysql-query-browser-1.1.9/mysql-query-browser/library/tests/test_query_analyze'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/bjl/mysql-query-browser-1.1.9.tar.gz_FILES/mysql-query-browser-1.1.9/mysql-query-browser/library/tests/test_query_analyze'
Making all in test_query_composition
make[3]: Entering directory `/home/bjl/mysql-query-browser-1.1.9.tar.gz_FILES/mysql-query-browser-1.1.9/mysql-query-browser/library/tests/test_query_composition'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/bjl/mysql-query-browser-1.1.9.tar.gz_FILES/mysql-query-browser-1.1.9/mysql-query-browser/library/tests/test_query_composition'Making all in test_strip_sql
make[3]: Entering directory `/home/bjl/mysql-query-browser-1.1.9.tar.gz_FILES/mysql-query-browser-1.1.9/mysql-query-browser/library/tests/test_strip_sql'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/bjl/mysql-query-browser-1.1.9.tar.gz_FILES/mysql-query-browser-1.1.9/mysql-query-browser/library/tests/test_strip_sql'
make[3]: Entering directory `/home/bjl/mysql-query-browser-1.1.9.tar.gz_FILES/mysql-query-browser-1.1.9/mysql-query-browser/library/tests'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/bjl/mysql-query-browser-1.1.9.tar.gz_FILES/mysql-query-browser-1.1.9/mysql-query-browser/library/tests'
make[2]: Leaving directory `/home/bjl/mysql-query-browser-1.1.9.tar.gz_FILES/mysql-query-browser-1.1.9/mysql-query-browser/library/tests'
make[2]: Entering directory `/home/bjl/mysql-query-browser-1.1.9.tar.gz_FILES/mysql-query-browser-1.1.9/mysql-query-browser/library'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/bjl/mysql-query-browser-1.1.9.tar.gz_FILES/mysql-query-browser-1.1.9/mysql-query-browser/library'
make[1]: Leaving directory `/home/bjl/mysql-query-browser-1.1.9.tar.gz_FILES/mysql-query-browser-1.1.9/mysql-query-browser/library'
Making all in source
make[1]: Entering directory `/home/bjl/mysql-query-browser-1.1.9.tar.gz_FILES/mysql-query-browser-1.1.9/mysql-query-browser/source'
Making all in linux
make[2]: Entering directory `/home/bjl/mysql-query-browser-1.1.9.tar.gz_FILES/mysql-query-browser-1.1.9/mysql-query-browser/source/linux'
cd ../.. && /bin/sh /home/bjl/mysql-query-browser-1.1.9.tar.gz_FILES/mysql-query-browser-1.1.9/mysql-query-browser/missing --run autoheader
rm -f stamp-h1
touch config.h.in
cd ../.. && /bin/sh ./config.status source/linux/config.h
config.status: creating source/linux/config.h
config.status: source/linux/config.h is unchanged
make all-am
make[3]: Entering directory `/home/bjl/mysql-query-browser-1.1.9.tar.gz_FILES/mysql-query-browser-1.1.9/mysql-query-browser/source/linux'
if g++ -DHAVE_CONFIG_H -I. -I. -I. -DXTHREADS -pthread -DORBIT2=1 -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libgtkhtml-3.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libgnomeprint-2.2 -I/usr/include/libgnomeprintui-2.2 -I/usr/include/gal-2.0 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/libbonoboui-2.0 -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/bonobo-activation-2.0 -I/usr/include/gtkmm-2.0 -I/usr/lib/gtkmm-2.0/include -I/usr/lib/sigc++-1.2/include -I/usr/include/sigc++-1.2 -I/usr/include/mysql -DBIG_JOINS=1 -I../../../mysql-gui-common/source/linux -I../../../mysql-gui-common/library/include -I../../../mysql-gui-common/library/shared_include -I../../library/include -I../../source/linux/gtksourceview -DPREFIX=\"""\" -DDATADIRNAME=\""share"\" -DCOMMONDIRNAME=\""common"\" -g -O2 -MT MGResultSetModel.o -MD -MP -MF ".deps/MGResultSetModel.Tpo" -c -o MGResultSetModel.o MGResultSetModel.cc; \
then mv -f ".deps/MGResultSetModel.Tpo" ".deps/MGResultSetModel.Po"; else rm -f ".deps/MGResultSetModel.Tpo"; exit 1; fi
MGResultSetModel.cc: In member function `virtual bool
MGResultSetModel::iter_next_vfunc(GtkTreeIter*)':
MGResultSetModel.cc:116: warning: cast from pointer to integer of different
size
MGResultSetModel.cc:116: warning: cast to pointer from integer of different
size
MGResultSetModel.cc:117: warning: cast from pointer to integer of different
size
MGResultSetModel.cc: In member function `virtual bool
MGResultSetModel::iter_nth_child_vfunc(GtkTreeIter*, const GtkTreeIter*,
int)':
MGResultSetModel.cc:156: warning: cast to pointer from integer of different
size
MGResultSetModel.cc: In member function `virtual Gtk::TreePath
MGResultSetModel::get_path_vfunc(const Gtk::TreeIter&)':
MGResultSetModel.cc:190: warning: cast from pointer to integer of different
size
MGResultSetModel.cc: In member function `virtual bool
MGResultSetModel::get_iter_vfunc(GtkTreeIter*, const Gtk::TreePath&)':
MGResultSetModel.cc:220: warning: cast to pointer from integer of different
size
MGResultSetModel.cc: In member function `bool MGResultSetModel::get_value(const
Gtk::TreeIter&, unsigned int, void*&, guint&)':
MGResultSetModel.cc:232: warning: cast from pointer to integer of different
size
MGResultSetModel.cc: In member function `virtual void
MGResultSetModel::get_value_vfunc(const Gtk::TreeIter&, int, GValue*)':
MGResultSetModel.cc:313: warning: cast from pointer to integer of different
size
MGResultSetModel.cc:367: error: no matching function for call to `
MGResultSetModel::get_value(const Gtk::TreeIter&, int&, void*&, gsize&)'
MGResultSetModel.cc:227: error: candidates are: bool
MGResultSetModel::get_value(const Gtk::TreeIter&, unsigned int, void*&,
guint&)
MGResultSetModel.cc: In member function `void MGResultSetModel::set_value(const
Gtk::TreeIter&, int, void*, unsigned int)':
MGResultSetModel.cc:402: warning: cast from pointer to integer of different
size
MGResultSetModel.cc: In member function `MYX_RS_ROW*
MGResultSetModel::get_iter_row(const Gtk::TreeIter&)':
MGResultSetModel.cc:479: warning: cast from pointer to integer of different
size
MGResultSetModel.cc: In member function `Gtk::TreeIter
MGResultSetModel::append()':
MGResultSetModel.cc:490: warning: cast to pointer from integer of different
size
MGResultSetModel.cc: In member function `void MGResultSetModel::erase(const
Gtk::TreeIter&)':
MGResultSetModel.cc:501: warning: cast from pointer to integer of different
size
make[3]: *** [MGResultSetModel.o] Error 1
make[3]: Leaving directory `/home/bjl/mysql-query-browser-1.1.9.tar.gz_FILES/mysql-query-browser-1.1.9/mysql-query-browser/source/linux'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/bjl/mysql-query-browser-1.1.9.tar.gz_FILES/mysql-query-browser-1.1.9/mysql-query-browser/source/linux'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bjl/mysql-query-browser-1.1.9.tar.gz_FILES/mysql-query-browser-1.1.9/mysql-query-browser/source'
make: *** [all-recursive] Error 1
[email]bjl@hephaistos:~/mysql-query-browser-1.1.9.tar.gz[/email]_FILES/mysql-query-browser-1.1.9/mysql-query-browser$

---

