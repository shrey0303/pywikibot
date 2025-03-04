Current release
---------------

Improvements
^^^^^^^^^^^^

* Add :meth:`site.APISite.ratelimit()<pywikibot.site._apisite.APISite.ratelimit>` method
  and :class:`tools.collections.RateLimit` NamedTuple (:phab:`T304808`)
* L10N Updates
* Add :class:`pagegenerators.PagePilePageGenerator` (:phab:`T353086`)

Bugfixes
^^^^^^^^

* Suppress error in :meth:`cosmetic_changes.CosmeticChangesToolkit.cleanUpLinks` (:phab:`T337045`)
* :func:`pywikibot.input_choice` validates *default* parameter (:phab:`T353097`)
* Remove typing imports from user-config.py file (:phab:`T352965`)

Breaking changes and code cleanups
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

* ``keys()`` and ``items()`` methods of :class:`data.api.Reques` gives a view instead a list (:phab:`T310953`)
* ``SequenceOutputter.format_list()`` was removed in favour of :attr:`tools.formatter.SequenceOutputter.out` property
* *output* parameter of :class:`bot_choice.OutputProxyOption` (i.e. ``OutputOption`` instance) without *out* property is no longer supported
* ``OutputOption.output()`` method was removed
* ``ContextOption.output_range()`` and ``HighlightContextOption.output_range()`` methods were removed
* ``page.url2unicode()`` function was removed in favour of :func:`tools.chars.url2string`
* *iterables* of :func:`tools.itertools.intersect_generators` must not be given as a single list or tuple;
  either consecutive iterables must be used or '*' to unpack
* *allow_duplicates* parameter of :func:`tools.itertools.intersect_generators` must be given as keyword argument
* Infinite rotating file handler with ``config.logfilesize`` of -1 is no longer supported
* ``Throttle.multiplydelay`` attribute was removed
* Python 3.6 support was dropped (:phab:`T347026`)


Deprecations
------------

* 9.0.0: ``pywikibot.version.get_toolforge_hostname()`` is deprecated without replacement
* 9.0.0: ``iteritems`` method of :class:`data.api.Request` will be removed in favour of ``items``
* 9.0.0: ``SequenceOutputter.output()`` is deprecated in favour of :attr:`tools.formatter.SequenceOutputter.out` property
* 9.0.0: *nullcontext* context manager and *SimpleQueue* queue of :mod:`backports` are derecated
* 8.4.0: *modules_only_mode* parameter of :class:`data.api.ParamInfo`, its *paraminfo_keys* class attribute
  and its preloaded_modules property will be removed
* 8.4.0: *dropdelay* and *releasepid* attributes of :class:`throttle.Throttle` will be removed
  in favour of *expiry* class attribute
* 8.2.0: :func:`tools.itertools.itergroup` will be removed in favour of :func:`backports.batched`
* 8.2.0: *normalize* parameter of :meth:`WbTime.toTimestr` and :meth:`WbTime.toWikibase` will be removed
* 8.1.0: Dependency of :exc:`exceptions.NoSiteLinkError` from :exc:`exceptions.NoPageError` will be removed
* 8.1.0: ``exceptions.Server414Error`` is deprecated in favour of :exc:`exceptions.Client414Error`
* 8.0.0: :meth:`Timestamp.clone()<pywikibot.time.Timestamp.clone>` method is deprecated
  in favour of ``Timestamp.replace()`` method.
* 8.0.0: :meth:`family.Family.maximum_GET_length` method is deprecated in favour of
  :ref:`config.maximum_GET_length<Account Settings>` (:phab:`T325957`)
* 8.0.0: ``addOnly`` parameter of :func:`textlib.replaceLanguageLinks` and
  :func:`textlib.replaceCategoryLinks` are deprecated in favour of ``add_only``
* 8.0.0: :class:`textlib.TimeStripper` regex attributes ``ptimeR``, ``ptimeznR``, ``pyearR``, ``pmonthR``,
  ``pdayR`` are deprecated in favour of ``patterns`` attribute which is a
  :class:`textlib.TimeStripperPatterns`.
* 8.0.0: :class:`textlib.TimeStripper` ``groups`` attribute is deprecated in favour of ``textlib.TIMEGROUPS``
* 8.0.0: :meth:`LoginManager.get_login_token<login.ClientLoginManager.get_login_token>` was
  replaced by ``login.ClientLoginManager.site.tokens['login']``
* 8.0.0: ``data.api.LoginManager()`` is deprecated in favour of :class:`login.ClientLoginManager`
* 8.0.0: :meth:`APISite.messages()<pywikibot.site._apisite.APISite.messages>` method is deprecated in favour of
  :attr:`userinfo['messages']<pywikibot.site._apisite.APISite.userinfo>`
* 8.0.0: :meth:`Page.editTime()<page.BasePage.editTime>` method is deprecated and should be replaced by
  :attr:`Page.latest_revision.timestamp<page.BasePage.latest_revision>`


Will be removed in Pywikibot 10
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

* 7.7.0: :mod:`tools.threading` classes should no longer imported from :mod:`tools`
* 7.6.0: :mod:`tools.itertools` datatypes should no longer imported from :mod:`tools`
* 7.6.0: :mod:`tools.collections` datatypes should no longer imported from :mod:`tools`
* 7.5.0: :mod:`textlib`.tzoneFixedOffset class will be removed in favour of :class:`time.TZoneFixedOffset`
* 7.4.0: ``FilePage.usingPages()`` was renamed to :meth:`using_pages()<pywikibot.FilePage.using_pages>`
* 7.2.0: ``tb`` parameter of :func:`exception()<pywikibot.exception>` function was renamed to ``exc_info``
* 7.2.0: XMLDumpOldPageGenerator is deprecated in favour of a ``content`` parameter of
  :func:`XMLDumpPageGenerator<pagegenerators.XMLDumpPageGenerator>` (:phab:`T306134`)
* 7.2.0: RedirectPageBot and NoRedirectPageBot bot classes are deprecated in favour of
  :attr:`use_redirects<bot.BaseBot.use_redirects>` attribute
* 7.2.0: :func:`tools.formatter.color_format<tools.formatter.color_format>` is deprecated and will be removed
* 7.1.0: Unused ``get_redirect`` parameter of :meth:`Page.getOldVersion()<page.BasePage.getOldVersion>` will be removed
* 7.0.0: User.isBlocked() method is renamed to is_blocked for consistency
* 7.0.0: A boolean watch parameter in Page.save() is deprecated and will be desupported
* 7.0.0: baserevid parameter of editSource(), editQualifier(), removeClaims(), removeSources(), remove_qualifiers() DataSite methods will be removed
* 7.0.0: Values of APISite.allpages() parameter filterredir other than True, False and None are deprecated
* 7.0.0: The i18n identifier 'cosmetic_changes-append' will be removed in favour of 'pywikibot-cosmetic-changes'
