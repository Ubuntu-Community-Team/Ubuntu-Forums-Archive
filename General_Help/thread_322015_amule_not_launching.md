---
title: "amule not launching"
date: 2006-12-19
forum: General Help
---

### Post by Corvair on 2006-12-19
I am going to try again, since I did not get a response to fix the problem I and also others are experiencing.
After having been requested to upgrade aMule, which I accepted, I cannot launch aMule anymore. This is very anoying since this upgrade should have been tested and working before sending out for upgrading.

This is what I get for a result after trying to launch from Terminal.

Can anyone help?????

A solution should be clear as I am not a computer analist.


amule: Symbol `_ZTV11wxSpinEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV14wxTextCtrlBase' has different size in shared object, consider re-linking
amule: Symbol `_ZTV16wxDatagramSocket' has different size in shared object, consider re-linking
amule: Symbol `_ZTV8wxSlider' has different size in shared object, consider re-linking
amule: Symbol `_ZTV14wxSocketServer' has different size in shared object, consider re-linking
amule: Symbol `_ZTV7wxTimer' has different size in shared object, consider re-linking
amule: Symbol `_ZTV14wxCommandEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV18wxGenericValidator' has different size in shared object, consider re-linking
amule: Symbol `_ZTV20wxNavigationKeyEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV12wxFocusEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV6wxMenu' has different size in shared object, consider re-linking
amule: Symbol `_ZTV7wxImage' has different size in shared object, consider re-linking
amule: Symbol `_ZTV17wxGenericListCtrl' has different size in shared object, consider re-linking
amule: Symbol `_ZTV16wxScrolledWindow' has different size in shared object, consider re-linking
amule: Symbol `_ZTV13wxSocketEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxTreeCtrl' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxListItem' has different size in shared object, consider re-linking
amule: Symbol `_ZTV12wxTimerEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV7wxGauge' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxListBase' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxRadioBox' has different size in shared object, consider re-linking
amule: Symbol `_ZTV8wxChoice' has different size in shared object, consider re-linking
amule: Symbol `_ZTV11wxListEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV11wxImageList' has different size in shared object, consider re-linking
amule: Symbol `_ZTV8wxObject' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxClientDC' has different size in shared object, consider re-linking
amule: Symbol `_ZTV13wxNotifyEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV15wxNotebookEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV5wxPen' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxMenuBase' has different size in shared object, consider re-linking
amule: Symbol `_ZTV14wxBitmapButton' has different size in shared object, consider re-linking
amule: Symbol `_ZTV16wxZipInputStream' has different size in shared object, consider re-linking
amule: Symbol `_ZTV7wxFrame' has different size in shared object, consider re-linking
amule: Symbol `_ZTV8wxButton' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxTextCtrl' has different size in shared object, consider re-linking
amule: Symbol `_ZTV8wxBitmap' has different size in shared object, consider re-linking
amule: Symbol `_ZTV6wxFont' has different size in shared object, consider re-linking
amule: Symbol `_ZTV12wxCloseEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV6wxIcon' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxSpinCtrl' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxCheckBox' has different size in shared object, consider re-linking
amule: Symbol `_ZTV18wxGenericImageList' has different size in shared object, consider re-linking
amule: Symbol `_ZTV16wxSplitterWindow' has different size in shared object, consider re-linking
amule: Symbol `_ZTV9wxControl' has different size in shared object, consider re-linking
amule: Symbol `_ZTV16wxTopLevelWindow' has different size in shared object, consider re-linking
amule: Symbol `_ZTV7wxBrush' has different size in shared object, consider re-linking
amule: Symbol `_ZTV12wxMouseEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV7wxPanel' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxListCtrl' has different size in shared object, consider re-linking
amule: Symbol `_ZTV8wxColour' has different size in shared object, consider re-linking
amule: Symbol `_ZTV17wxGenericTreeCtrl' has different size in shared object, consider re-linking
Fatal Error: Mismatch between the program and library build versions detected.
The library used 2.6 (no debug,Unicode,compiler with C++ ABI 1002,wx containers),
and your program used 2.6 (no debug,Unicode,compiler with C++ ABI 1002,wx containers,compatible with 2.4).
Aborted

---

### Post by Corvair on 2006-12-23
For anyone interrestsed or who had the same problem,
I went on aMule forum and found out that the problem was with wxGTK.

So I went to Synaptic and completely removed wxGTK.

Now I am able to launch aMule.

At first it would not connect so I loaded wxGTK from the site wxgtkwidget.org and installed it in tmp file.
Now everything seems to work fine.

---

