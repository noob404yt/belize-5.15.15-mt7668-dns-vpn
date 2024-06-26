# ---------------------------------------------------
# Compile Options
# Edited by noob404 (ps4linux.com)
# ---------------------------------------------------
export CONFIG_MTK_COMBO_WIFI_HIF=sdio
export MODULE_NAME=wlan_mt76x8_sdio
WLAN_CHIP_LIST:=-UMT6620 -UMT6628 -UMT5931 -UMT6630 -UMT6632
ccflags-y += $(WLAN_CHIP_LIST)

#WLAN_CHIP_ID=$(MTK_COMBO_CHIP)
ifeq ($(WLAN_CHIP_ID),)
    WLAN_CHIP_ID := MT6632
endif

ccflags-y += -DCFG_SUPPORT_DEBUG_FS=0
ccflags-y += -DWLAN_INCLUDE_PROC
ccflags-y += -DCFG_ANDROID_AOSP_PRIV_CMD
ccflags-y += -DCFG_SUPPORT_AGPS_ASSIST=1
ccflags-y += -DCFG_SUPPORT_TSF_USING_BOOTTIME=1
ccflags-y += -Werror
ccflags-y += -Wno-implicit-fallthrough
ccflags-y += -Wno-error=declaration-after-statement
ccflags-y += -Wno-unused-function
ccflags-y:=$(filter-out -U$(WLAN_CHIP_ID),$(ccflags-y))
ccflags-y += -DLINUX -D$(WLAN_CHIP_ID)

# Enables options to fix WiFi and DNS errors - noob404
ccflags-y += -DCFG_SUPPORT_CFG80211_AUTH=0
ccflags-y += -DCFG_SUPPORT_SAE=0
ccflags-y += -DCFG_SUPPORT_OWE=0
ccflags-y += -DCFG_SUPPORT_SUITB=0
ccflags-y += -DCFG_SUPPORT_DBDC_TC6=1
ccflags-y += -DCFG_SUPPORT_DFS_MASTER=1
ccflags-y += -DCFG_SUPPORT_LARGE_TX_PWR_LIMIT_TABLE=0
ccflags-y += -DCFG_CHIP_RESET_SUPPORT=1
ccflags-y += -DCFG_TX_WMM_ENHANCE=0
ccflags-y += -DCFG_SUPPORT_SAP_DFS_CHANNEL=0
ccflags-y += -DCFG_IPI_2CHAIN_SUPPORT=0
ccflags-y += -DBUILD_DBG_MSG=0
ccflags-y += -DCFG_ENABLE_PS_INTV_CTRL=0
ccflags-y += -DCFG_ENABLE_1RPD_MMPS_CTRL=0
ccflags-y += -DCFG_ENABLE_DEWEIGHTING_CTRL=0
ccflags-y += -DCFG_NUM_DIFFERENT_CHANNELS_STA=1
ccflags-y += -DCFG_NUM_DIFFERENT_CHANNELS_P2P=1
ccflags-y += -DCFG_DRIVER_INITIAL_RUNNING_MODE=3
ccflags-y += -DCFG_ENABLE_WAKE_LOCK=0
ccflags-y += -DCFG_DEFAULT_DBG_LEVEL=0xF
ccflags-y += -DCFG_TX_DIRECT_USB=1
ccflags-y += -DCFG_RX_DIRECT_USB=1
ccflags-y += -DCFG_USB_REQ_TX_DATA_FFA_CNT=10
ccflags-y += -DCFG_USB_REQ_TX_DATA_CNT=2
ccflags-y += -DCFG_USB_REQ_RX_DATA_CNT=2
ccflags-y += -DCFG_ENABLE_EFUSE_MAC_ADDR=0
ccflags-y += -DCFG_SUPPORT_SINGLE_SKU_LOCAL_DB=0
ccflags-y += -DCFG_SCAN_CHANNEL_SPECIFIED=1
ccflags-y += -DCFG_SUPPORT_ROAMING=0
ccflags-y += -DCFG_SUPPORT_SAME_BSS_REASSOC=0
ccflags-y += -DCFG_P2P_SCAN_REPORT_ALL_BSS=0
ccflags-y += -DCFG_DRIVER_INF_NAME_CHANGE=n
ccflags-y += -DCFG_RX_SINGLE_CHAIN_SUPPORT=0
ccflags-y += -DCFG_SUPPORT_AGPS_ASSIST=1
ccflags-y += -DCFG_SUPPORT_TSF_USING_BOOTTIME=1
ccflags-y += -DCONFIG_MTK_WIFI_MCC_SUPPORT=y
ccflags-y += -DMTK_MET_PROFILING_SUPPORT=yes
ccflags-y += -DMTK_MET_TAG_SUPPORT=0
ccflags-y += -DCFG_DUMP_TXPOWR_TABLE=n
ccflags-y += -DCFG_SUPPORT_DISABLE_BCN_HINTS=n

DRIVER_BUILD_DATE=$(shell date +%Y%m%d%H%M%S)
ccflags-y += -DDRIVER_BUILD_DATE='"$(DRIVER_BUILD_DATE)"'

ccflags-y += -DCFG_SUPPORT_CHNL_CONFLICT_REVISE=0
ccflags-y += -DCFG_SUPPORT_AEE=0
ccflags-y += -DBUILD_QA_DBG=1
ccflags-y += -DCFG_BUILT_IN_DRIVER=1
ccflags-y += -DCFG_WPS_DISCONNECT=1
ccflags-y += -DCFG_SUPPORT_PASSPOINT=1
ccflags-y += -DCFG_HS20_DEBUG=0
ccflags-y += -DCFG_ENABLE_GTK_FRAME_FILTER=0
ccflags-y += -DCFG_SUPPORT_DUAL_CARD_DUAL_DRIVER=0
ccflags-y += -DCFG_SUPPORT_RSSI_COMP=0
ccflags-y += -DCFG_EFUSE_AUTO_MODE_SUPPORT=0
ccflags-y += -DCFG_SUPPORT_BFER=0
ccflags-y += -DCFG_KEY_ERROR_STATISTIC_RECOVERY=0
ccflags-y += -DCFG_IOCTL_WAIT_FOR_COMPLETION_TIMEOUT=0
ccflags-y += -DCFG_GARP_KEEPALIVE=0
ccflags-y += -DCFG_SUPPORT_PWR_LIMIT_FILE_LOAD

ifeq ($(CONFIG_MTK_COMBO_WIFI_HIF), sdio)
	ccflags-y += -D_HIF_SDIO=1
else ifeq ($(CONFIG_MTK_COMBO_WIFI_HIF), pcie)
    ccflags-y += -D_HIF_PCIE=1
else ifeq ($(CONFIG_MTK_COMBO_WIFI_HIF), usb)
	ccflags-y += -D_HIF_USB=1
else
    $(error Unsuppoted HIF=$(CONFIG_MTK_COMBO_WIFI_HIF)!!)
endif

ifneq ($(CFG_CFG80211_VERSION),)
VERSION_STR = $(subst ",,$(subst ., , $(subst -, ,$(subst v,,$(CFG_CFG80211_VERSION)))))
$(info VERSION_STR=$(VERSION_STR))
X = $(firstword $(VERSION_STR))
Y = $(word 2 ,$(VERSION_STR))
Z = $(word 3 ,$(VERSION_STR))
VERSION := $(shell echo "$$(( $X * 65536 + $Y * 256 + $Z))" )
ccflags-y += -DCFG_CFG80211_VERSION=$(VERSION)
$(info DCFG_CFG80211_VERSION=$(VERSION))
endif

MTK_MET_PROFILING_SUPPORT = yes
ifeq ($(MTK_MET_PROFILING_SUPPORT), yes)
    ccflags-y += -DCFG_MET_PACKET_TRACE_SUPPORT=1
else
    ccflags-y += -DCFG_MET_PACKET_TRACE_SUPPORT=0
endif

MTK_MET_TAG_SUPPORT = no
ifeq ($(MTK_MET_TAG_SUPPORT), yes)
    ccflags-y += -DMET_USER_EVENT_SUPPORT
    ccflags-y += -DCFG_MET_TAG_SUPPORT=1
else
    ccflags-y += -DCFG_MET_TAG_SUPPORT=0
endif

ifeq ($(MODULE_NAME),)
	MODULE_NAME := wlan_$(shell echo $(strip $(WLAN_CHIP_ID)) | tr A-Z a-z)_$(CONFIG_MTK_COMBO_WIFI_HIF)
endif

ccflags-y += -DDBG=0
ccflags-y += -I$(src)/os -I$(src)/os/linux/include
ccflags-y += -I$(src)/include -I$(src)/include/nic -I$(src)/include/mgmt -I$(src)/include/chips
ifeq ($(CONFIG_MTK_COMBO_WIFI_HIF), sdio)
ccflags-y += -I$(src)/os/linux/hif/sdio/include
else ifeq ($(CONFIG_MTK_COMBO_WIFI_HIF), pcie)
ccflags-y += -I$(src)/os/linux/hif/pcie/include
else ifeq ($(CONFIG_MTK_COMBO_WIFI_HIF), usb)
ccflags-y += -I$(src)/os/linux/hif/usb/include
endif

ifneq ($(PLATFORM_FLAGS), )
    ccflags-y += $(PLATFORM_FLAGS)
endif

ifeq ($(CONFIG_MTK_WIFI_ONLY),$(filter $(CONFIG_MTK_WIFI_ONLY),m y))
obj-$(CONFIG_MTK_WIFI_ONLY) += $(MODULE_NAME).o
else
obj-$(CONFIG_MTK_COMBO_WIFI) += $(MODULE_NAME).o
#obj-y += $(MODULE_NAME).o
endif

# ---------------------------------------------------
# Directory List
# ---------------------------------------------------
COMMON_DIR  := common/
OS_DIR      := os/linux/
ifeq ($(CONFIG_MTK_COMBO_WIFI_HIF), sdio)
HIF_DIR	    := os/linux/hif/sdio/
else ifeq ($(CONFIG_MTK_COMBO_WIFI_HIF), pcie)
HIF_DIR     := os/linux/hif/pcie/
else ifeq ($(CONFIG_MTK_COMBO_WIFI_HIF), usb)
HIF_DIR	    := os/linux/hif/usb/
endif
NIC_DIR     := nic/
MGMT_DIR    := mgmt/
CHIPS       := chips/


# ---------------------------------------------------
# Objects List
# ---------------------------------------------------

COMMON_OBJS :=	$(COMMON_DIR)dump.o \
	       		$(COMMON_DIR)wlan_lib.o \
	       		$(COMMON_DIR)wlan_oid.o \
	       		$(COMMON_DIR)wlan_bow.o

NIC_OBJS := $(NIC_DIR)nic.o \
			$(NIC_DIR)nic_tx.o \
			$(NIC_DIR)nic_rx.o \
			$(NIC_DIR)nic_pwr_mgt.o \
            $(NIC_DIR)nic_rate.o \
			$(NIC_DIR)cmd_buf.o \
			$(NIC_DIR)que_mgt.o \
			$(NIC_DIR)nic_cmd_event.o \
			$(NIC_DIR)nic_umac.o

OS_OBJS :=	$(OS_DIR)gl_init.o \
			$(OS_DIR)gl_kal.o  \
			$(OS_DIR)gl_bow.o \
			$(OS_DIR)gl_wext.o \
			$(OS_DIR)gl_wext_priv.o \
			$(OS_DIR)gl_ate_agent.o \
			$(OS_DIR)gl_qa_agent.o \
			$(OS_DIR)gl_hook_api.o \
			$(OS_DIR)gl_rst.o \
			$(OS_DIR)gl_cfg80211.o \
			$(OS_DIR)gl_proc.o \
			$(OS_DIR)gl_vendor.o \
			$(OS_DIR)platform.o

MGMT_OBJS := $(MGMT_DIR)ais_fsm.o \
			 $(MGMT_DIR)aaa_fsm.o \
			 $(MGMT_DIR)assoc.o \
			 $(MGMT_DIR)auth.o \
			 $(MGMT_DIR)bss.o \
			 $(MGMT_DIR)cnm.o \
			 $(MGMT_DIR)cnm_timer.o \
			 $(MGMT_DIR)cnm_mem.o \
			 $(MGMT_DIR)hem_mbox.o \
			 $(MGMT_DIR)mib.o \
			 $(MGMT_DIR)privacy.o  \
			 $(MGMT_DIR)rate.o \
			 $(MGMT_DIR)rlm.o \
			 $(MGMT_DIR)rlm_domain.o \
			 $(MGMT_DIR)reg_rule.o \
			 $(MGMT_DIR)rlm_obss.o \
			 $(MGMT_DIR)rlm_protection.o \
			 $(MGMT_DIR)rsn.o \
			 $(MGMT_DIR)saa_fsm.o \
			 $(MGMT_DIR)scan.o \
			 $(MGMT_DIR)scan_fsm.o \
             $(MGMT_DIR)swcr.o \
             $(MGMT_DIR)roaming_fsm.o \
             $(MGMT_DIR)tkip_mic.o \
             $(MGMT_DIR)hs20.o \
             $(MGMT_DIR)tdls.o

CHIPS_OBJS := $(CHIPS)mt6632.o \
			  $(CHIPS)mt7668.o
# ---------------------------------------------------
# P2P Objects List
# ---------------------------------------------------

COMMON_OBJS += $(COMMON_DIR)wlan_p2p.o

NIC_OBJS += $(NIC_DIR)p2p_nic.o

OS_OBJS += $(OS_DIR)gl_p2p.o \
           $(OS_DIR)gl_p2p_cfg80211.o \
           $(OS_DIR)gl_p2p_init.o \
           $(OS_DIR)gl_p2p_kal.o

MGMT_OBJS += $(MGMT_DIR)p2p_dev_fsm.o\
            $(MGMT_DIR)p2p_dev_state.o\
            $(MGMT_DIR)p2p_role_fsm.o\
            $(MGMT_DIR)p2p_role_state.o\
            $(MGMT_DIR)p2p_func.o\
            $(MGMT_DIR)p2p_scan.o\
            $(MGMT_DIR)p2p_ie.o\
            $(MGMT_DIR)p2p_rlm.o\
            $(MGMT_DIR)p2p_assoc.o\
            $(MGMT_DIR)p2p_bss.o\
            $(MGMT_DIR)p2p_rlm_obss.o\
            $(MGMT_DIR)p2p_fsm.o

MGMT_OBJS += $(MGMT_DIR)wapi.o

ifeq ($(CONFIG_MTK_COMBO_WIFI_HIF), sdio)
HIF_OBJS :=  $(HIF_DIR)arm.o \
             $(HIF_DIR)sdio.o \
             $(HIF_DIR)sdio_test_driver_core.o \
             $(HIF_DIR)sdio_test_driver_ops.o
else ifeq ($(CONFIG_MTK_COMBO_WIFI_HIF), pcie)
HIF_OBJS :=  $(HIF_DIR)arm.o \
             $(HIF_DIR)pcie.o
else ifeq ($(CONFIG_MTK_COMBO_WIFI_HIF), usb)
HIF_OBJS :=  $(HIF_DIR)usb.o
endif

HIF_OBJS +=  $(HIF_DIR)hal_api.o

$(MODULE_NAME)-objs  += $(COMMON_OBJS)
$(MODULE_NAME)-objs  += $(NIC_OBJS)
$(MODULE_NAME)-objs  += $(OS_OBJS)
$(MODULE_NAME)-objs  += $(HIF_OBJS)
$(MODULE_NAME)-objs  += $(MGMT_OBJS)
$(MODULE_NAME)-objs  += $(CHIPS_OBJS)

#
# mtprealloc
#
ifeq ($(CONFIG_MTK_PREALLOC_MEMORY), y)
ccflags-y += -DCFG_PREALLOC_MEMORY
ccflags-y += -I$(src)/prealloc/include
MODULE_NAME_PREALLOC = $(MODULE_NAME)_prealloc
PREALLOC_OBJS := prealloc/prealloc.o
$(MODULE_NAME_PREALLOC)-objs += $(PREALLOC_OBJS)
obj-m += $(MODULE_NAME_PREALLOC).o
endif
