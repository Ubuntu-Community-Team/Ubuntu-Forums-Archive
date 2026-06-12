---
title: "ccPublisher"
date: 2008-05-24
forum: General Help
---

### Post by Neovos on 2008-05-24
Trying to install ccPublisher version 2.2.1 on my Hardy Laptop and coming up with some errors. Anyone familiar with this program at all?

The site says I need:
* Python 2.4 or later
* wxPython 2.6 or later
* elementtree for Python

and I installed:
Python 2.5.2
python-wxgtk2.8
python-wxversion
python-elementtree

My installation looks like this:

```
brian@Apollo:~/Desktop$ tar zxvf ccPublisher-2.2.1.tar.gz
ccPublisher-2.2.1/
ccPublisher-2.2.1/ccpublisher/
ccPublisher-2.2.1/ccpublisher/ui/
ccPublisher-2.2.1/ccpublisher/ui/__init__.py
ccPublisher-2.2.1/ccpublisher/ui/ia.py
ccPublisher-2.2.1/ccpublisher/ui/selfhost.py
ccPublisher-2.2.1/ccpublisher/ui/welcome.py
ccPublisher-2.2.1/ccpublisher/__init__.py
ccPublisher-2.2.1/ccpublisher/adapters.py
ccPublisher-2.2.1/ccpublisher/app.py
ccPublisher-2.2.1/ccpublisher/configure.zcml
ccPublisher-2.2.1/ccpublisher/const.py
ccPublisher-2.2.1/ccpublisher/ia.py
ccPublisher-2.2.1/ccpublisher/interfaces.py
ccPublisher-2.2.1/ccpublisher/metadata.py
ccPublisher-2.2.1/ccpublisher/selfhost.py
ccPublisher-2.2.1/ccpublisher/validators.py
ccPublisher-2.2.1/ccrdf/
ccPublisher-2.2.1/ccrdf/__init__.py
ccPublisher-2.2.1/ccrdf/aaronrdf.py
ccPublisher-2.2.1/ccrdf/ccrdf.py
ccPublisher-2.2.1/ccrdf/rdfdict.py
ccPublisher-2.2.1/ccrdf/rdfextract.py
ccPublisher-2.2.1/cctagutils/
ccPublisher-2.2.1/cctagutils/filetypes/
ccPublisher-2.2.1/cctagutils/filetypes/__init__.py
ccPublisher-2.2.1/cctagutils/filetypes/mp3.py
ccPublisher-2.2.1/cctagutils/__init__.py
ccPublisher-2.2.1/cctagutils/base32.py
ccPublisher-2.2.1/cctagutils/cli.py
ccPublisher-2.2.1/cctagutils/const.py
ccPublisher-2.2.1/cctagutils/interfaces.py
ccPublisher-2.2.1/cctagutils/lookup.py
ccPublisher-2.2.1/cctagutils/metadata.py
ccPublisher-2.2.1/cctagutils/rdf.py
ccPublisher-2.2.1/ccwsclient/
ccPublisher-2.2.1/ccwsclient/__init__.py
ccPublisher-2.2.1/ccwsclient/rest.py
ccPublisher-2.2.1/ccwx/
ccPublisher-2.2.1/ccwx/__init__.py
ccPublisher-2.2.1/ccwx/stext.py
ccPublisher-2.2.1/ccwx/wraptext.py
ccPublisher-2.2.1/ccwx/xpapp.py
ccPublisher-2.2.1/ccwx/xrc.py
ccPublisher-2.2.1/ccwx/xrcwiz.py
ccPublisher-2.2.1/deploy/
ccPublisher-2.2.1/deploy/linux/
ccPublisher-2.2.1/deploy/linux/__init__.py
ccPublisher-2.2.1/deploy/linux/ccpublisher.desktop.in
ccPublisher-2.2.1/deploy/linux/msgfmt.py
ccPublisher-2.2.1/deploy/linux/msgmerge.py
ccPublisher-2.2.1/deploy/linux/straw_distutils.py
ccPublisher-2.2.1/deploy/__init__.py
ccPublisher-2.2.1/deploy/setupcfg.py
ccPublisher-2.2.1/deploy/setupsupport.py
ccPublisher-2.2.1/eyeD3/
ccPublisher-2.2.1/eyeD3/__init__.py
ccPublisher-2.2.1/eyeD3/binfuncs.py
ccPublisher-2.2.1/eyeD3/frames.py
ccPublisher-2.2.1/eyeD3/mp3.py
ccPublisher-2.2.1/eyeD3/tag.py
ccPublisher-2.2.1/eyeD3/utils.py
ccPublisher-2.2.1/libfeedback/
ccPublisher-2.2.1/libfeedback/__init__.py
ccPublisher-2.2.1/libfeedback/comm.py
ccPublisher-2.2.1/libfeedback/wxsupportwiz.py
ccPublisher-2.2.1/p6/
ccPublisher-2.2.1/p6/app/
ccPublisher-2.2.1/p6/app/support/
ccPublisher-2.2.1/p6/app/support/__init__.py
ccPublisher-2.2.1/p6/app/support/browser.py
ccPublisher-2.2.1/p6/app/__init__.py
ccPublisher-2.2.1/p6/app/bananas.py
ccPublisher-2.2.1/p6/app/extension.py
ccPublisher-2.2.1/p6/app/interfaces.py
ccPublisher-2.2.1/p6/app/wxpy.py
ccPublisher-2.2.1/p6/configure/
ccPublisher-2.2.1/p6/configure/__init__.py
ccPublisher-2.2.1/p6/configure/meta.zcml
ccPublisher-2.2.1/p6/configure/metaconfigure.py
ccPublisher-2.2.1/p6/configure/metadirectives.py
ccPublisher-2.2.1/p6/extension/
ccPublisher-2.2.1/p6/extension/__init__.py
ccPublisher-2.2.1/p6/extension/events.py
ccPublisher-2.2.1/p6/extension/exceptions.py
ccPublisher-2.2.1/p6/extension/interfaces.py
ccPublisher-2.2.1/p6/extension/point.py
ccPublisher-2.2.1/p6/i18n/
ccPublisher-2.2.1/p6/i18n/__init__.py
ccPublisher-2.2.1/p6/i18n/catalog.py
ccPublisher-2.2.1/p6/i18n/msgfmt.py
ccPublisher-2.2.1/p6/i18n/translate.py
ccPublisher-2.2.1/p6/metadata/
ccPublisher-2.2.1/p6/metadata/__init__.py
ccPublisher-2.2.1/p6/metadata/adapters.py
ccPublisher-2.2.1/p6/metadata/base.py
ccPublisher-2.2.1/p6/metadata/configure.zcml
ccPublisher-2.2.1/p6/metadata/events.py
ccPublisher-2.2.1/p6/metadata/interfaces.py
ccPublisher-2.2.1/p6/metadata/license.py
ccPublisher-2.2.1/p6/metadata/persistance.py
ccPublisher-2.2.1/p6/metadata/types.py
ccPublisher-2.2.1/p6/storage/
ccPublisher-2.2.1/p6/storage/providers/
ccPublisher-2.2.1/p6/storage/providers/__init__.py
ccPublisher-2.2.1/p6/storage/providers/id3.py
ccPublisher-2.2.1/p6/storage/__init__.py
ccPublisher-2.2.1/p6/storage/adapters.py
ccPublisher-2.2.1/p6/storage/basic.py
ccPublisher-2.2.1/p6/storage/common.py
ccPublisher-2.2.1/p6/storage/configure.zcml
ccPublisher-2.2.1/p6/storage/events.py
ccPublisher-2.2.1/p6/storage/interfaces.py
ccPublisher-2.2.1/p6/storage/items.py
ccPublisher-2.2.1/p6/ui/
ccPublisher-2.2.1/p6/ui/pages/
ccPublisher-2.2.1/p6/ui/pages/__init__.py
ccPublisher-2.2.1/p6/ui/pages/fieldrender.py
ccPublisher-2.2.1/p6/ui/pages/fileselector.py
ccPublisher-2.2.1/p6/ui/pages/finalurl.py
ccPublisher-2.2.1/p6/ui/pages/license.py
ccPublisher-2.2.1/p6/ui/pages/metadata.py
ccPublisher-2.2.1/p6/ui/pages/storageselector.py
ccPublisher-2.2.1/p6/ui/pages/store.py
ccPublisher-2.2.1/p6/ui/pages/xml.py
ccPublisher-2.2.1/p6/ui/pages/xrcpage.py
ccPublisher-2.2.1/p6/ui/windows/
ccPublisher-2.2.1/p6/ui/windows/__init__.py
ccPublisher-2.2.1/p6/ui/windows/prefs.py
ccPublisher-2.2.1/p6/ui/__init__.py
ccPublisher-2.2.1/p6/ui/adapters.py
ccPublisher-2.2.1/p6/ui/configure.zcml
ccPublisher-2.2.1/p6/ui/events.py
ccPublisher-2.2.1/p6/ui/fields.py
ccPublisher-2.2.1/p6/ui/interfaces.py
ccPublisher-2.2.1/p6/ui/wizard.py
ccPublisher-2.2.1/p6/ui/wrappers.py
ccPublisher-2.2.1/p6/zcmlsupport/
ccPublisher-2.2.1/p6/zcmlsupport/browser/
ccPublisher-2.2.1/p6/zcmlsupport/browser/configure.zcml
ccPublisher-2.2.1/p6/zcmlsupport/browser/meta.zcml
ccPublisher-2.2.1/p6/zcmlsupport/__init__.py
ccPublisher-2.2.1/p6/zcmlsupport/adapter.py
ccPublisher-2.2.1/p6/zcmlsupport/configure.zcml
ccPublisher-2.2.1/p6/zcmlsupport/contentdirective.py
ccPublisher-2.2.1/p6/zcmlsupport/fields.py
ccPublisher-2.2.1/p6/zcmlsupport/hooks.py
ccPublisher-2.2.1/p6/zcmlsupport/interface.py
ccPublisher-2.2.1/p6/zcmlsupport/meta.zcml
ccPublisher-2.2.1/p6/zcmlsupport/metaconfigure.py
ccPublisher-2.2.1/p6/zcmlsupport/metadirectives.py
ccPublisher-2.2.1/p6/zcmlsupport/registration.py
ccPublisher-2.2.1/p6/zcmlsupport/site.py
ccPublisher-2.2.1/p6/zcmlsupport/testing.py
ccPublisher-2.2.1/p6/zcmlsupport/vocabulary.py
ccPublisher-2.2.1/p6/__init__.py
ccPublisher-2.2.1/p6/api.py
ccPublisher-2.2.1/p6/configure.zcml
ccPublisher-2.2.1/p6/meta.zcml
ccPublisher-2.2.1/pyarchive/
ccPublisher-2.2.1/pyarchive/__init__.py
ccPublisher-2.2.1/pyarchive/cb_ftp.py
ccPublisher-2.2.1/pyarchive/const.py
ccPublisher-2.2.1/pyarchive/exceptions.py
ccPublisher-2.2.1/pyarchive/identifier.py
ccPublisher-2.2.1/pyarchive/mp3.py
ccPublisher-2.2.1/pyarchive/submission.py
ccPublisher-2.2.1/pyarchive/user.py
ccPublisher-2.2.1/pyarchive/utils.py
ccPublisher-2.2.1/rdflib/
ccPublisher-2.2.1/rdflib/backends/
ccPublisher-2.2.1/rdflib/backends/Concurrent.py
ccPublisher-2.2.1/rdflib/backends/InMemoryBackend.py
ccPublisher-2.2.1/rdflib/backends/SleepyCatBackend.py
ccPublisher-2.2.1/rdflib/backends/__init__.py
ccPublisher-2.2.1/rdflib/model/
ccPublisher-2.2.1/rdflib/model/__init__.py
ccPublisher-2.2.1/rdflib/model/schema.py
ccPublisher-2.2.1/rdflib/syntax/
ccPublisher-2.2.1/rdflib/syntax/parsers/
ccPublisher-2.2.1/rdflib/syntax/parsers/NTParser.py
ccPublisher-2.2.1/rdflib/syntax/parsers/RDFXMLHandler.py
ccPublisher-2.2.1/rdflib/syntax/parsers/RDFXMLParser.py
ccPublisher-2.2.1/rdflib/syntax/parsers/__init__.py
ccPublisher-2.2.1/rdflib/syntax/serializers/
ccPublisher-2.2.1/rdflib/syntax/serializers/N3Serializer.py
ccPublisher-2.2.1/rdflib/syntax/serializers/NTSerializer.py
ccPublisher-2.2.1/rdflib/syntax/serializers/XMLSerializer.py
ccPublisher-2.2.1/rdflib/syntax/serializers/YAMLSerializer.py
ccPublisher-2.2.1/rdflib/syntax/serializers/__init__.py
ccPublisher-2.2.1/rdflib/syntax/__init__.py
ccPublisher-2.2.1/rdflib/syntax/parser.py
ccPublisher-2.2.1/rdflib/syntax/serializer.py
ccPublisher-2.2.1/rdflib/syntax/xml_names.py
ccPublisher-2.2.1/rdflib/BNode.py
ccPublisher-2.2.1/rdflib/Identifier.py
ccPublisher-2.2.1/rdflib/InformationStore.py
ccPublisher-2.2.1/rdflib/Literal.py
ccPublisher-2.2.1/rdflib/Namespace.py
ccPublisher-2.2.1/rdflib/RDF.py
ccPublisher-2.2.1/rdflib/Store.py
ccPublisher-2.2.1/rdflib/StringInputSource.py
ccPublisher-2.2.1/rdflib/TripleStore.py
ccPublisher-2.2.1/rdflib/URIRef.py
ccPublisher-2.2.1/rdflib/URLInputSource.py
ccPublisher-2.2.1/rdflib/__init__.py
ccPublisher-2.2.1/rdflib/constants.py
ccPublisher-2.2.1/rdflib/exceptions.py
ccPublisher-2.2.1/rdflib/util.py
ccPublisher-2.2.1/resources/
ccPublisher-2.2.1/resources/locale/
ccPublisher-2.2.1/resources/locale/ca_ES/
ccPublisher-2.2.1/resources/locale/ca_ES/ccpublisher.po
ccPublisher-2.2.1/resources/locale/ca_ES/p6.po
ccPublisher-2.2.1/resources/locale/en_US/
ccPublisher-2.2.1/resources/locale/en_US/ccpublisher.mo
ccPublisher-2.2.1/resources/locale/en_US/ccpublisher.po
ccPublisher-2.2.1/resources/locale/en_US/p6.mo
ccPublisher-2.2.1/resources/locale/en_US/p6.po
ccPublisher-2.2.1/resources/locale/es_ES/
ccPublisher-2.2.1/resources/locale/es_ES/ccpublisher.po
ccPublisher-2.2.1/resources/locale/es_ES/p6.po
ccPublisher-2.2.1/resources/locale/hr_HR/
ccPublisher-2.2.1/resources/locale/hr_HR/ccpublisher.mo
ccPublisher-2.2.1/resources/locale/hr_HR/ccpublisher.po
ccPublisher-2.2.1/resources/locale/hr_HR/p6.mo
ccPublisher-2.2.1/resources/locale/hr_HR/p6.po
ccPublisher-2.2.1/resources/locale/pl_PL/
ccPublisher-2.2.1/resources/locale/pl_PL/ccpublisher.po
ccPublisher-2.2.1/resources/locale/pl_PL/p6.po
ccPublisher-2.2.1/resources/locale/zh_TW/
ccPublisher-2.2.1/resources/locale/zh_TW/ccpublisher.po
ccPublisher-2.2.1/resources/locale/zh_TW/p6.po
ccPublisher-2.2.1/resources/locale/ccpublisher.pot
ccPublisher-2.2.1/resources/locale/p6.pot
ccPublisher-2.2.1/resources/LICENSE.txt
ccPublisher-2.2.1/resources/app.zcml
ccPublisher-2.2.1/resources/cc.icns
ccPublisher-2.2.1/resources/cc.ico
ccPublisher-2.2.1/resources/cc_33.gif
ccPublisher-2.2.1/resources/cc_doc_33.gif
ccPublisher-2.2.1/resources/ccp8.icns
ccPublisher-2.2.1/resources/ccp8.ico
ccPublisher-2.2.1/resources/ccpublisher.xrc
ccPublisher-2.2.1/resources/extprefs.conf
ccPublisher-2.2.1/resources/p6.xrc
ccPublisher-2.2.1/resources/publishguy.gif
ccPublisher-2.2.1/resources/publishguy_small.gif
ccPublisher-2.2.1/resources/version.txt
ccPublisher-2.2.1/tagger/
ccPublisher-2.2.1/tagger/__init__.py
ccPublisher-2.2.1/tagger/constants.py
ccPublisher-2.2.1/tagger/debug.py
ccPublisher-2.2.1/tagger/encoding.py
ccPublisher-2.2.1/tagger/exceptions.py
ccPublisher-2.2.1/tagger/id3v1.py
ccPublisher-2.2.1/tagger/id3v2.py
ccPublisher-2.2.1/tagger/id3v2frame.py
ccPublisher-2.2.1/tagger/utility.py
ccPublisher-2.2.1/zope/
ccPublisher-2.2.1/zope/component/
ccPublisher-2.2.1/zope/component/bbb/
ccPublisher-2.2.1/zope/component/bbb/tests/
ccPublisher-2.2.1/zope/component/bbb/tests/__init__.py
ccPublisher-2.2.1/zope/component/bbb/tests/components.py
ccPublisher-2.2.1/zope/component/bbb/tests/placelesssetup.py
ccPublisher-2.2.1/zope/component/bbb/tests/request.py
ccPublisher-2.2.1/zope/component/bbb/tests/test_adapter.py
ccPublisher-2.2.1/zope/component/bbb/tests/test_api.py
ccPublisher-2.2.1/zope/component/bbb/tests/test_service.py
ccPublisher-2.2.1/zope/component/bbb/tests/test_utilityservice.py
ccPublisher-2.2.1/zope/component/bbb/__init__.py
ccPublisher-2.2.1/zope/component/bbb/adapter.py
ccPublisher-2.2.1/zope/component/bbb/contextdependent.py
ccPublisher-2.2.1/zope/component/bbb/exceptions.py
ccPublisher-2.2.1/zope/component/bbb/interfaces.py
ccPublisher-2.2.1/zope/component/bbb/service.py
ccPublisher-2.2.1/zope/component/bbb/servicenames.py
ccPublisher-2.2.1/zope/component/bbb/utility.py
ccPublisher-2.2.1/zope/component/__init__.py
ccPublisher-2.2.1/zope/component/factory.py
ccPublisher-2.2.1/zope/component/interfaces.py
ccPublisher-2.2.1/zope/component/site.py
ccPublisher-2.2.1/zope/component/testing.py
ccPublisher-2.2.1/zope/component/tests.py
ccPublisher-2.2.1/zope/configuration/
ccPublisher-2.2.1/zope/configuration/__init__.py
ccPublisher-2.2.1/zope/configuration/config.py
ccPublisher-2.2.1/zope/configuration/docutils.py
ccPublisher-2.2.1/zope/configuration/exceptions.py
ccPublisher-2.2.1/zope/configuration/fields.py
ccPublisher-2.2.1/zope/configuration/interfaces.py
ccPublisher-2.2.1/zope/configuration/name.py
ccPublisher-2.2.1/zope/configuration/stxdocs.py
ccPublisher-2.2.1/zope/configuration/xmlconfig.py
ccPublisher-2.2.1/zope/configuration/zopeconfigure.py
ccPublisher-2.2.1/zope/deprecation/
ccPublisher-2.2.1/zope/deprecation/__init__.py
ccPublisher-2.2.1/zope/deprecation/deprecation.py
ccPublisher-2.2.1/zope/deprecation/tests.py
ccPublisher-2.2.1/zope/event/
ccPublisher-2.2.1/zope/event/__init__.py
ccPublisher-2.2.1/zope/event/tests.py
ccPublisher-2.2.1/zope/exceptions/
ccPublisher-2.2.1/zope/exceptions/__init__.py
ccPublisher-2.2.1/zope/exceptions/_duplicate.py
ccPublisher-2.2.1/zope/exceptions/_notfounderror.py
ccPublisher-2.2.1/zope/exceptions/exceptionformatter.py
ccPublisher-2.2.1/zope/exceptions/interfaces.py
ccPublisher-2.2.1/zope/i18nmessageid/
ccPublisher-2.2.1/zope/i18nmessageid/__init__.py
ccPublisher-2.2.1/zope/i18nmessageid/message.py
ccPublisher-2.2.1/zope/i18nmessageid/messageid.py
ccPublisher-2.2.1/zope/i18nmessageid/tests.py
ccPublisher-2.2.1/zope/interface/
ccPublisher-2.2.1/zope/interface/common/
ccPublisher-2.2.1/zope/interface/common/__init__.py
ccPublisher-2.2.1/zope/interface/common/idatetime.py
ccPublisher-2.2.1/zope/interface/common/interfaces.py
ccPublisher-2.2.1/zope/interface/common/mapping.py
ccPublisher-2.2.1/zope/interface/common/sequence.py
ccPublisher-2.2.1/zope/interface/__init__.py
ccPublisher-2.2.1/zope/interface/_flatten.py
ccPublisher-2.2.1/zope/interface/adapter.py
ccPublisher-2.2.1/zope/interface/advice.py
ccPublisher-2.2.1/zope/interface/declarations.py
ccPublisher-2.2.1/zope/interface/document.py
ccPublisher-2.2.1/zope/interface/exceptions.py
ccPublisher-2.2.1/zope/interface/interface.py
ccPublisher-2.2.1/zope/interface/interfaces.py
ccPublisher-2.2.1/zope/interface/ro.py
ccPublisher-2.2.1/zope/interface/verify.py
ccPublisher-2.2.1/zope/schema/
ccPublisher-2.2.1/zope/schema/__init__.py
ccPublisher-2.2.1/zope/schema/_bootstrapfields.py
ccPublisher-2.2.1/zope/schema/_bootstrapinterfaces.py
ccPublisher-2.2.1/zope/schema/_field.py
ccPublisher-2.2.1/zope/schema/_schema.py
ccPublisher-2.2.1/zope/schema/accessors.py
ccPublisher-2.2.1/zope/schema/fieldproperty.py
ccPublisher-2.2.1/zope/schema/interfaces.py
ccPublisher-2.2.1/zope/schema/vocabulary.py
ccPublisher-2.2.1/zope/testing/
ccPublisher-2.2.1/zope/testing/__init__.py
ccPublisher-2.2.1/zope/testing/cleanup.py
ccPublisher-2.2.1/zope/testing/doctest.py
ccPublisher-2.2.1/zope/testing/doctestunit.py
ccPublisher-2.2.1/zope/testing/formparser.py
ccPublisher-2.2.1/zope/testing/loggingsupport.py
ccPublisher-2.2.1/zope/testing/loghandler.py
ccPublisher-2.2.1/zope/testing/module.py
ccPublisher-2.2.1/zope/testing/renormalizing.py
ccPublisher-2.2.1/zope/testing/testrunner.py
ccPublisher-2.2.1/zope/testing/tests.py
ccPublisher-2.2.1/zope/__init__.py
ccPublisher-2.2.1/README.txt
ccPublisher-2.2.1/ccPublisher.sh
ccPublisher-2.2.1/ccp.py
ccPublisher-2.2.1/setup.cfg
ccPublisher-2.2.1/setup.py
ccPublisher-2.2.1/sitecustomize.py
ccPublisher-2.2.1/PKG-INFO
brian@Apollo:~/Desktop$ cd ccPublisher-2.2.1
brian@Apollo:~/Desktop/ccPublisher-2.2.1$ ./ccPublisher.sh
Traceback (most recent call last):
  File "ccp.py", line 15, in <module>
    import ccpublisher.const as const
  File "/home/brian/Desktop/ccPublisher-2.2.1/ccpublisher/const.py", line 8, in <module>
    import p6.api
  File "/home/brian/Desktop/ccPublisher-2.2.1/p6/__init__.py", line 29, in <module>
    import metadata
  File "/home/brian/Desktop/ccPublisher-2.2.1/p6/metadata/__init__.py", line 6, in <module>
    import adapters
  File "/home/brian/Desktop/ccPublisher-2.2.1/p6/metadata/adapters.py", line 7, in <module>
    import zope.component
  File "/home/brian/Desktop/ccPublisher-2.2.1/zope/component/__init__.py", line 23, in <module>
    from zope.component.interfaces import IComponentArchitecture
  File "/home/brian/Desktop/ccPublisher-2.2.1/zope/component/interfaces.py", line 24, in <module>
    from zope.exceptions import NotFoundError
  File "/home/brian/Desktop/ccPublisher-2.2.1/zope/exceptions/__init__.py", line 37, in <module>
    from zope.exceptions._notfounderror import NotFoundError, INotFoundError
  File "/home/brian/Desktop/ccPublisher-2.2.1/zope/exceptions/_notfounderror.py", line 21, in <module>
    from zope.interface.common.interfaces import IKeyError
  File "/home/brian/Desktop/ccPublisher-2.2.1/zope/interface/common/interfaces.py", line 80, in <module>
    classImplements(OverflowWarning, IOverflowWarning)
NameError: name 'OverflowWarning' is not defined

```

Then needless to say, nothing happened after that. Any ideas?

---

### Post by jkeogh on 2009-05-30
Same problem in kubuntu 9.04

default@notebook:/cfg/ccPublisher-2.2.1$ python -V
Python 2.6.2
default@notebook:/cfg/ccPublisher-2.2.1$ ./ccPublisher.sh
Traceback (most recent call last):
  File "ccp.py", line 15, in <module>
    import ccpublisher.const as const
  File "/cfg/ccPublisher-2.2.1/ccpublisher/const.py", line 8, in <module>
    import p6.api
  File "/cfg/ccPublisher-2.2.1/p6/__init__.py", line 29, in <module>
    import metadata
  File "/cfg/ccPublisher-2.2.1/p6/metadata/__init__.py", line 6, in <module>
    import adapters
  File "/cfg/ccPublisher-2.2.1/p6/metadata/adapters.py", line 7, in <module>
    import zope.component
  File "/cfg/ccPublisher-2.2.1/zope/component/__init__.py", line 23, in <module>
    from zope.component.interfaces import IComponentArchitecture
  File "/cfg/ccPublisher-2.2.1/zope/component/interfaces.py", line 24, in <module>
    from zope.exceptions import NotFoundError
  File "/cfg/ccPublisher-2.2.1/zope/exceptions/__init__.py", line 37, in <module>
    from zope.exceptions._notfounderror import NotFoundError, INotFoundError
  File "/cfg/ccPublisher-2.2.1/zope/exceptions/_notfounderror.py", line 21, in <module>
    from zope.interface.common.interfaces import IKeyError
  File "/cfg/ccPublisher-2.2.1/zope/interface/common/interfaces.py", line 80, in <module>
    classImplements(OverflowWarning, IOverflowWarning)
NameError: name 'OverflowWarning' is not defined

---

### Post by quetzalzun on 2009-06-11
Same case, I think I have the programs and have the same "overfowarning", any sugestions?

---

