DIR := $(shell mktemp -d)

srpm:
	#git clone https://gitlab.com/redhat/centos-stream/rpms/compat-openssl11 -b c9s $(DIR)
	wget -O $(DIR)/openssl11.src.rpm https://dl.rockylinux.org/pub/rocky/9/devel/source/tree/Packages/c/compat-openssl11-1.1.1k-5.el9_6.1.src.rpm
	rpm2archive $(DIR)/openssl11.src.rpm
	tar xvf $(DIR)/openssl11.src.rpm.tgz -C $(DIR)
	cat update-spec-format.patch | patch -p1 -d $(DIR)
	rpmbuild --define "_sourcedir $(DIR)" --define "_srcrpmdir $(outdir)" -bs $(DIR)/compat-openssl11.spec
