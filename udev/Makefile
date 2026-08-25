all:

install:
	mkdir -p $(DESTDIR)$(SYSLIBDIR)/udev/rules.d
	cp udev-qubes-block.rules $(DESTDIR)$(SYSLIBDIR)/udev/rules.d/99-qubes-block.rules
	cp udev-qubes-usb.rules $(DESTDIR)$(SYSLIBDIR)/udev/rules.d/99-qubes-usb.rules
	cp udev-qubes-vbd.rules $(DESTDIR)$(SYSLIBDIR)/udev/rules.d/99-qubes-vbd.rules
	cp udev-qubes-misc.rules $(DESTDIR)$(SYSLIBDIR)/udev/rules.d/99-qubes-misc.rules
	cp udev-qubes-dmroot.rules $(DESTDIR)$(SYSLIBDIR)/udev/rules.d/90-qubes-dmroot.rules
	mkdir -p $(DESTDIR)$(SYSLIBDIR)/tmpfiles.d
	cp xen-devices-qubes.conf $(DESTDIR)$(SYSLIBDIR)/tmpfiles.d/xen-devices-qubes.conf

	mkdir -p $(DESTDIR)$(SCRIPTSDIR)
	cp udev-block-add-change $(DESTDIR)$(SCRIPTSDIR)
	cp udev-block-remove $(DESTDIR)$(SCRIPTSDIR)
	cp udev-usb-add-change $(DESTDIR)$(SCRIPTSDIR)
	cp udev-usb-remove $(DESTDIR)$(SCRIPTSDIR)
	cp qubes-block-mount-watcher $(DESTDIR)$(SCRIPTSDIR)

ifeq (1,${DEBIANBUILD})
	mkdir -p $(DESTDIR)/lib/systemd/system
	install -m 0644 qubes-block-mount-watcher.service \
		$(DESTDIR)/lib/systemd/system/
else
	mkdir -p $(DESTDIR)/usr/lib/systemd/system
	install -m 0644 qubes-block-mount-watcher.service \
		$(DESTDIR)/usr/lib/systemd/system/

	mkdir -p $(DESTDIR)/usr/lib/systemd/system-preset
	install -m 0644 qubes-block-mount-watcher.preset \
		$(DESTDIR)/usr/lib/systemd/system-preset/75-qubes-block-mount-watcher.preset
endif

	mkdir -p $(DESTDIR)/etc/qubes-rpc
	cp qubes.RefreshBlockDevices $(DESTDIR)/etc/qubes-rpc
