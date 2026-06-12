---
title: "Cannot Compile MonoDevelop 1.0"
date: 2008-03-17
forum: General Help
---

### Post by mcr-joe on 2008-03-17
I get this before it fails:
```
make[3]: Entering directory `/home/mcr-joe/Code/monodevelop-1.0/src/core/MonoDevelop.Core.Gui'
/usr/bin/gmcs -debug -codepage:utf8 -out:../../../build/bin/MonoDevelop.Core.Gui.dll -target:library -r:/usr/local/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/glade-sharp.dll -r:/usr/local/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/pango-sharp.dll -r:/usr/local/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/atk-sharp.dll -r:/usr/local/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gdk-sharp.dll -r:/usr/local/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gtk-sharp.dll -r:/usr/local/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/glib-sharp.dll   -r:/usr/local/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/pango-sharp.dll -r:/usr/local/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/atk-sharp.dll -r:/usr/local/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gdk-sharp.dll -r:/usr/local/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gtk-sharp.dll -r:/usr/local/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/glib-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gnome-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/art-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gnome-vfs-sharp.dll   -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gnome-vfs-sharp.dll   -r:/usr/local/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/pango-sharp.dll -r:/usr/local/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/atk-sharp.dll -r:/usr/local/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gdk-sharp.dll -r:/usr/local/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gtk-sharp.dll -r:/usr/local/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/glib-sharp.dll   -r:/usr/local/lib/mono/mono-addins/Mono.Addins.Gui.dll -r:/usr/local/lib/mono/mono-addins/Mono.Addins.dll   -r:/usr/local/lib/mono/mono-addins/Mono.Addins.dll   -r:/usr/local/lib/mono/mono-addins/Mono.Addins.Setup.dll -r:/usr/local/lib/mono/mono-addins/Mono.Addins.dll   -r:../../../build/bin/MonoDevelop.Components.dll -r:../../../build/bin/MonoDevelop.Core.dll -r:ICSharpCode.SharpZipLib -r:Mono.Posix -r:System -r:System.Drawing -r:System.Xml /resource:./Base.glade /resource:./gtk-gui/gui.stetic /resource:./icons/BreakPoint.png /resource:./icons/build-project-16.png /resource:./icons/build-project-22.png /resource:./icons/build-solution-16.png /resource:./icons/build-solution-22.png /resource:./icons/comment.png /resource:./icons/edit-select-all.png /resource:./icons/edit-select-all_22.png /resource:./icons/element-class-16.png /resource:./icons/element-delegate-16.png /resource:./icons/element-enumeration-16.png /resource:./icons/element-event-16.png /resource:./icons/element-field-16.png /resource:./icons/element-interface-16.png /resource:./icons/element-literal-16.png /resource:./icons/element-method-16.png /resource:./icons/element-namespace-16.png /resource:./icons/element-property-16.png /resource:./icons/element-structure-16.png /resource:./icons/ExecutionMarker.png /resource:./icons/file-class-32.png /resource:./icons/file-enum-32.png /resource:./icons/file-interface-32.png /resource:./icons/file-struct-32.png /resource:./icons/file-xml-32.png /resource:./icons/GeneralWizardBackground /resource:./icons/gnome-fs-regular.png /resource:./icons/Icons.16x16.ClearAllBookmarks /resource:./icons/Icons.16x16.CloseAllDocuments /resource:./icons/Icons.16x16.CloseCombineIcon /resource:./icons/Icons.16x16.ClosedFolderBitmap /resource:./icons/Icons.16x16.ClosedReferenceFolder /resource:./icons/Icons.16x16.ClosedResourceFolder /resource:./icons/Icons.16x16.CombineIcon /resource:./icons/Icons.16x16.Empty /resource:./icons/Icons.16x16.FindInFiles /resource:./icons/Icons.16x16.FindNextIcon /resource:./icons/Icons.16x16.GotoNextbookmark /resource:./icons/Icons.16x16.GotoPrevbookmark /resource:./icons/Icons.16x16.MiscFiles /resource:./icons/Icons.16x16.NewCombineIcon.png /resource:./icons/Icons.16x16.NewFolderIcon /resource:./icons/Icons.16x16.NewSolutionIcon.png /resource:./icons/Icons.16x16.OpenFolderBitmap /resource:./icons/Icons.16x16.OpenProjectIcon /resource:./icons/Icons.16x16.OpenReferenceFolder /resource:./icons/Icons.16x16.OpenResourceFolder /resource:./icons/Icons.16x16.OutputIcon /resource:./icons/Icons.16x16.Reference /resource:./icons/Icons.16x16.ReplaceInFiles /resource:./icons/Icons.16x16.ResourceFileIcon /resource:./icons/Icons.16x16.SaveAllIcon /resource:./icons/Icons.16x16.SplitWindow /resource:./icons/Icons.16x16.TextFileIcon /resource:./icons/Icons.16x16.TipOfTheDay /resource:./icons/Icons.16x16.ToggleBookmark /resource:./icons/Icons.16x16.WebSearchIcon /resource:./icons/Icons.16x16.XMLFileIcon /resource:./icons/Icons.22x22.ClearAllBookmarks.png /resource:./icons/Icons.22x22.GotoNextbookmark.png /resource:./icons/Icons.22x22.GotoPrevbookmark.png /resource:./icons/Icons.22x22.ToggleBookmark.png /resource:./icons/Icons.24x24.SaveAllIcon /resource:./icons/Icons.32x32.EmptyFileIcon /resource:./icons/Icons.32x32.HTMLFileIcon /resource:./icons/Icons.32x32.ResourceFileIcon /resource:./icons/Icons.32x32.TextFileIcon /resource:./icons/Icons.32x32.XMLFileIcon /resource:./icons/Icons.SharpDevelopIcon /resource:./icons/Icons.SharpDevelopIcon-22.png /resource:./icons/package-x-generic.png /resource:./icons/package-x-generic_22.png /resource:./icons/pad-task-list-16.png /resource:./icons/plugin-16.png /resource:./icons/plugin-22.png /resource:./icons/plugin-32.png /resource:./icons/project-16.png /resource:./icons/project-32.png /resource:./icons/project-console-32.png /resource:./icons/project-gui-32.png /resource:./icons/project-library-32.png /resource:./icons/solution-16.png /resource:./icons/solution-32.png /resource:./icons/system-software-update.png /resource:./icons/system-software-update_22.png /resource:./icons/uncomment.png /resource:./icons/user-package.png /resource:./icons/visibility-internal-16.png /resource:./icons/visibility-private-16.png /resource:./icons/visibility-protected-16.png /resource:./icons/visual-studio.png /resource:./icons/web-overlay-16.png /resource:./icons/web-overlay-32.png /resource:./icons/workspace-16.png /resource:./icons/workspace-32.png /resource:./MonoDevelop.Core.Gui.addin.xml ./gtk-gui/generated.cs ./gtk-gui/MonoDevelop.Core.Gui.Dialogs.MultiTaskProgressDialog.cs ./MonoDevelop.Core.Gui.Codons/DialogPanelCodon.cs ./MonoDevelop.Core.Gui.Codons/StockIconCodon.cs ./MonoDevelop.Core.Gui.Components/FileBrowser.cs ./MonoDevelop.Core.Gui.Components/MenuButtonEntry.cs ./MonoDevelop.Core.Gui.Dialogs/AbstractOptionPanel.cs ./MonoDevelop.Core.Gui.Dialogs/DefaultDialogPanelDescriptor.cs ./MonoDevelop.Core.Gui.Dialogs/ErrorDialog.cs ./MonoDevelop.Core.Gui.Dialogs/IDialogPanel.cs ./MonoDevelop.Core.Gui.Dialogs/IDialogPanelDescriptor.cs ./MonoDevelop.Core.Gui.Dialogs/MultiTaskProgressDialog.cs ./MonoDevelop.Core.Gui.Dialogs/ProgressDialog.cs ./MonoDevelop.Core.Gui.Dialogs/SetupApp.cs ./MonoDevelop.Core.Gui.Dialogs/TreeViewOptions.cs ./MonoDevelop.Core.Gui.ProgressMonitoring/BaseProgressMonitor.cs ./MonoDevelop.Core.Gui.ProgressMonitoring/MessageDialogProgressMonitor.cs ./MonoDevelop.Core.Gui.ProgressMonitoring/MultiTaskDialogProgressMonitor.cs ./MonoDevelop.Core.Gui.WebBrowser/IWebBrowser.cs ./MonoDevelop.Core.Gui.WebBrowser/IWebBrowserLoader.cs ./MonoDevelop.Core.Gui.WebBrowser/LoadingProgressChangedEventArgs.cs ./MonoDevelop.Core.Gui.WebBrowser/LocationChangedEventArgs.cs ./MonoDevelop.Core.Gui.WebBrowser/LocationChangingEventArgs.cs ./MonoDevelop.Core.Gui.WebBrowser/StatusMessageChangedEventArgs.cs ./MonoDevelop.Core.Gui.WebBrowser/TitleChangedEventArgs.cs ./MonoDevelop.Core.Gui/AsyncDispatchAttribute.cs ./MonoDevelop.Core.Gui/DefaultPlatformService.cs ./MonoDevelop.Core.Gui/DesktopApplication.cs ./MonoDevelop.Core.Gui/DispatchService.cs ./MonoDevelop.Core.Gui/FreeDispatchAttribute.cs ./MonoDevelop.Core.Gui/GuiService.cs ./MonoDevelop.Core.Gui/GuiSyncAbstractService.cs ./MonoDevelop.Core.Gui/GuiSyncContext.cs ./MonoDevelop.Core.Gui/GuiSyncObject.cs ./MonoDevelop.Core.Gui/IMementoCapable.cs ./MonoDevelop.Core.Gui/IMessageService.cs ./MonoDevelop.Core.Gui/ITextBufferStrategy.cs ./MonoDevelop.Core.Gui/MessageService.cs ./MonoDevelop.Core.Gui/PixbufList.cs ./MonoDevelop.Core.Gui/PlatformService.cs ./MonoDevelop.Core.Gui/RecentFileStorage.cs ./MonoDevelop.Core.Gui/RecentItem.cs ./MonoDevelop.Core.Gui/RecentOpen.cs ./MonoDevelop.Core.Gui/ResourceService.cs ./MonoDevelop.Core.Gui/StockIcons.cs ./MonoDevelop.Core.Gui/SyncContext.cs ./MonoDevelop.Core.Gui/SyncContextAttribute.cs ./MonoDevelop.Core.Gui/SyncObject.cs ./MonoDevelop.Core.Gui/WebBrowserService.cs AssemblyInfo.cs
./MonoDevelop.Core.Gui.Components/FileBrowser.cs(33,32): warning CS0612: `Gtk.Tooltips' is obsolete
./MonoDevelop.Core.Gui.Components/FileBrowser.cs(33,52): warning CS0612: `Gtk.Tooltips' is obsolete
./MonoDevelop.Core.Gui.Components/FileBrowser.cs(61,30): warning CS0612: `Gtk.ToolItem.SetTooltip(Gtk.Tooltips, string, string)' is obsolete
./MonoDevelop.Core.Gui.Components/FileBrowser.cs(66,32): warning CS0612: `Gtk.ToolItem.SetTooltip(Gtk.Tooltips, string, string)' is obsolete
./MonoDevelop.Core.Gui.Components/FileBrowser.cs(72,31): warning CS0612: `Gtk.ToolItem.SetTooltip(Gtk.Tooltips, string, string)' is obsolete
./MonoDevelop.Core.Gui/GuiService.cs(79,44): error CS1502: The best overloaded method match for `Mono.Addins.Gui.AddinManagerWindow.Run(Gtk.Window)' has some invalid arguments
./MonoDevelop.Core.Gui/GuiService.cs(79,44): error CS1503: Argument 1: Cannot convert from `Gtk.Window' to `Gtk.Window'
./MonoDevelop.Core.Gui/GuiService.cs(79,44): (equally named types possibly from different assemblies in previous error)
/usr/local/lib/mono/gac/gtk-sharp/2.12.0.0__35e10195dab3c99f/gtk-sharp.dll (Location of the symbol related to previous error)
/usr/lib/mono/gac/gtk-sharp/2.10.0.0__35e10195dab3c99f/gtk-sharp.dll (Location of the symbol related to previous error)
Compilation failed: 2 error(s), 5 warnings
make[3]: *** [../../../build/bin/MonoDevelop.Core.Gui.dll] Error 1
make[3]: Leaving directory `/home/mcr-joe/Code/monodevelop-1.0/src/core/MonoDevelop.Core.Gui'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mcr-joe/Code/monodevelop-1.0/src/core'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mcr-joe/Code/monodevelop-1.0/src'
make: *** [all-recursive] Error 1

```

---

### Post by penguinpi.com on 2008-03-17
Are you compiling it from source? I think you can just use apt.

sudo apt-get install mono mono-gmcs mono-gac mono-utils monodevelop monodoc-browser monodevelop-nunit monodevelop-versioncontrol

---

### Post by The Fiddler on 2008-03-17
I had the same problem. The solution is to use [gtk-sharp 2.10.4](http://go-mono.com/sources/gtk-sharp210/gtk-sharp-2.10.4.tar.bz2) instead of 2.8.x.

I uninstalled the later - it worked :)

---

### Post by zizzdude on 2008-03-23
> **penguinpi.com said:**
> Are you compiling it from source? I think you can just use apt.

sudo apt-get install mono mono-gmcs mono-gac mono-utils monodevelop monodoc-browser monodevelop-nunit monodevelop-versioncontrol

only problem is that you'd be installing monodevelop of an outdated version. :p

---

### Post by mcr-joe on 2008-03-25
Sorry, for not repling in awhile, but when's it comming out in the responsities?

---

