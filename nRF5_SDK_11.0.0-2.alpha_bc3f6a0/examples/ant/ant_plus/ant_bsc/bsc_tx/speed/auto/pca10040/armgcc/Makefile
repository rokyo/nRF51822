PROJECT_NAME := ant_bsc_tx_speed_auto_s212_pca10040

export OUTPUT_FILENAME
#MAKEFILE_NAME := $(CURDIR)/$(word $(words $(MAKEFILE_LIST)),$(MAKEFILE_LIST))
MAKEFILE_NAME := $(MAKEFILE_LIST)
MAKEFILE_DIR := $(dir $(MAKEFILE_NAME) ) 

TEMPLATE_PATH = ../../../../../../../../../components/toolchain/gcc
ifeq ($(OS),Windows_NT)
include $(TEMPLATE_PATH)/Makefile.windows
else
include $(TEMPLATE_PATH)/Makefile.posix
endif

MK := mkdir
RM := rm -rf

#echo suspend
ifeq ("$(VERBOSE)","1")
NO_ECHO := 
else
NO_ECHO := @
endif

# Toolchain commands
CC              := '$(GNU_INSTALL_ROOT)/bin/$(GNU_PREFIX)-gcc'
AS              := '$(GNU_INSTALL_ROOT)/bin/$(GNU_PREFIX)-as'
AR              := '$(GNU_INSTALL_ROOT)/bin/$(GNU_PREFIX)-ar' -r
LD              := '$(GNU_INSTALL_ROOT)/bin/$(GNU_PREFIX)-ld'
NM              := '$(GNU_INSTALL_ROOT)/bin/$(GNU_PREFIX)-nm'
OBJDUMP         := '$(GNU_INSTALL_ROOT)/bin/$(GNU_PREFIX)-objdump'
OBJCOPY         := '$(GNU_INSTALL_ROOT)/bin/$(GNU_PREFIX)-objcopy'
SIZE            := '$(GNU_INSTALL_ROOT)/bin/$(GNU_PREFIX)-size'

#function for removing duplicates in a list
remduplicates = $(strip $(if $1,$(firstword $1) $(call remduplicates,$(filter-out $(firstword $1),$1))))

#source common to all targets
C_SOURCE_FILES += \
$(abspath ../../../../../../../../../components/drivers_ext/segger_rtt/RTT_Syscalls_GCC.c) \
$(abspath ../../../../../../../../../components/drivers_ext/segger_rtt/SEGGER_RTT.c) \
$(abspath ../../../../../../../../../components/drivers_ext/segger_rtt/SEGGER_RTT_printf.c) \
$(abspath ../../../../../../../../../components/libraries/button/app_button.c) \
$(abspath ../../../../../../../../../components/libraries/util/app_error.c) \
$(abspath ../../../../../../../../../components/libraries/fifo/app_fifo.c) \
$(abspath ../../../../../../../../../components/libraries/timer/app_timer.c) \
$(abspath ../../../../../../../../../components/libraries/trace/app_trace.c) \
$(abspath ../../../../../../../../../components/libraries/util/nrf_assert.c) \
$(abspath ../../../../../../../../../components/libraries/util/nrf_log.c) \
$(abspath ../../../../../../../../../components/libraries/uart/retarget.c) \
$(abspath ../../../../../../../../../components/libraries/sensorsim/sensorsim.c) \
$(abspath ../../../../../../../../../components/libraries/uart/app_uart_fifo.c) \
$(abspath ../../../../../../../../../components/drivers_nrf/delay/nrf_delay.c) \
$(abspath ../../../../../../../../../components/drivers_nrf/common/nrf_drv_common.c) \
$(abspath ../../../../../../../../../components/drivers_nrf/gpiote/nrf_drv_gpiote.c) \
$(abspath ../../../../../../../../../components/drivers_nrf/uart/nrf_drv_uart.c) \
$(abspath ../../../../../../../../../components/ant/ant_profiles/ant_bsc/ant_bsc.c) \
$(abspath ../../../../../../../../../components/ant/ant_profiles/ant_bsc/pages/ant_bsc_combined_page_0.c) \
$(abspath ../../../../../../../../../components/ant/ant_profiles/ant_bsc/pages/ant_bsc_page_0.c) \
$(abspath ../../../../../../../../../components/ant/ant_profiles/ant_bsc/pages/ant_bsc_page_1.c) \
$(abspath ../../../../../../../../../components/ant/ant_profiles/ant_bsc/pages/ant_bsc_page_2.c) \
$(abspath ../../../../../../../../../components/ant/ant_profiles/ant_bsc/pages/ant_bsc_page_3.c) \
$(abspath ../../../../../../../../../components/ant/ant_profiles/ant_bsc/pages/ant_bsc_page_4.c) \
$(abspath ../../../../../../../../../components/ant/ant_profiles/ant_bsc/pages/ant_bsc_page_5.c) \
$(abspath ../../../../../../../../../components/ant/ant_profiles/ant_bsc/simulator/ant_bsc_simulator.c) \
$(abspath ../../../../../../../../../components/ant/ant_channel_config/ant_channel_config.c) \
$(abspath ../../../../../../../../../components/ant/ant_key_manager/ant_key_manager.c) \
$(abspath ../../../../../../../../../components/ant/ant_stack_config/ant_stack_config.c) \
$(abspath ../../../../../../../../../components/ant/ant_state_indicator/ant_state_indicator.c) \
$(abspath ../../../../../../../../bsp/bsp.c) \
$(abspath ../../../../../../../../bsp/bsp_btn_ant.c) \
$(abspath ../../../../main.c) \
$(abspath ../../../../../../../../../components/toolchain/system_nrf52.c) \
$(abspath ../../../../../../../../../components/softdevice/common/softdevice_handler/softdevice_handler.c) \

#assembly files common to all targets
ASM_SOURCE_FILES  = $(abspath ../../../../../../../../../components/toolchain/gcc/gcc_startup_nrf52.s)

#includes common to all targets
INC_PATHS  = -I$(abspath ../../../../config/ant_bsc_tx_speed_auto_s212_pca10040)
INC_PATHS += -I$(abspath ../../../../config)
INC_PATHS += -I$(abspath ../../../../../../../../../components/ant/ant_key_manager/config)
INC_PATHS += -I$(abspath ../../../../../../../../../components/ant/ant_profiles/ant_bsc)
INC_PATHS += -I$(abspath ../../../../../../../../../components/drivers_nrf/gpiote)
INC_PATHS += -I$(abspath ../../../../../../../../../components/ant/ant_state_indicator)
INC_PATHS += -I$(abspath ../../../../../../../../../components/toolchain)
INC_PATHS += -I$(abspath ../../../../../../../../../components/libraries/uart)
INC_PATHS += -I$(abspath ../../../../../../../../../components/drivers_nrf/common)
INC_PATHS += -I$(abspath ../../../../../../../../../components/softdevice/common/softdevice_handler)
INC_PATHS += -I$(abspath ../../../../../../../../../components/ant/ant_channel_config)
INC_PATHS += -I$(abspath ../../../../../../../../../components/toolchain/gcc)
INC_PATHS += -I$(abspath ../../../../../../../../../components/ant/ant_profiles/ant_bsc/pages)
INC_PATHS += -I$(abspath ../../../../../../../../../components/ant/ant_stack_config)
INC_PATHS += -I$(abspath ../../../../../../../../../components/libraries/fifo)
INC_PATHS += -I$(abspath ../../../../../../../../../components/drivers_nrf/uart)
INC_PATHS += -I$(abspath ../../../../../../../../../components/device)
INC_PATHS += -I$(abspath ../../../../../../../../../components/libraries/timer)
INC_PATHS += -I$(abspath ../../../../../../../../../components/drivers_nrf/config)
INC_PATHS += -I$(abspath ../../../../../../../../../components/libraries/util)
INC_PATHS += -I$(abspath ../../../../../../../../../components/drivers_nrf/hal)
INC_PATHS += -I$(abspath ../../../../../../../../../components/libraries/button)
INC_PATHS += -I$(abspath ../../../../../../../../bsp)
INC_PATHS += -I$(abspath ../../../../../../../../../components/drivers_ext/segger_rtt)
INC_PATHS += -I$(abspath ../../../../../../../../../components/ant/ant_profiles/ant_bsc/pages/logger)
INC_PATHS += -I$(abspath ../../../../../../../../../components/libraries/sensorsim)
INC_PATHS += -I$(abspath ../../../../../../../../../components/ant/ant_profiles/ant_bsc/simulator)
INC_PATHS += -I$(abspath ../../../../../../../../../components/softdevice/s212/headers/nrf52)
INC_PATHS += -I$(abspath ../../../../../../../../../components/libraries/trace)
INC_PATHS += -I$(abspath ../../../../../../../../../components/softdevice/s212/headers)
INC_PATHS += -I$(abspath ../../../../../../../../../components/drivers_nrf/delay)
INC_PATHS += -I$(abspath ../../../../../../../../../components/ant/ant_profiles/ant_bsc/utils)
INC_PATHS += -I$(abspath ../../../../../../../../../components/ant/ant_key_manager)

OBJECT_DIRECTORY = _build
LISTING_DIRECTORY = $(OBJECT_DIRECTORY)
OUTPUT_BINARY_DIRECTORY = $(OBJECT_DIRECTORY)

# Sorting removes duplicates
BUILD_DIRECTORIES := $(sort $(OBJECT_DIRECTORY) $(OUTPUT_BINARY_DIRECTORY) $(LISTING_DIRECTORY) )

#flags common to all targets
CFLAGS  = -DTRACE_BSC_PAGE_4_ENABLE
CFLAGS += -DNRF52
CFLAGS += -DTRACE_BSC_PAGE_5_ENABLE
CFLAGS += -DMODIFICATION_TYPE=1
CFLAGS += -DSOFTDEVICE_PRESENT
CFLAGS += -DBOARD_PCA10040
CFLAGS += -DTRACE_BSC_PAGE_1_ENABLE
CFLAGS += -DNRF52_PAN_12
CFLAGS += -DNRF52_PAN_15
CFLAGS += -DNRF52_PAN_58
CFLAGS += -DNRF52_PAN_55
CFLAGS += -DNRF52_PAN_54
CFLAGS += -DNRF52_PAN_31
CFLAGS += -DNRF52_PAN_30
CFLAGS += -DNRF52_PAN_51
CFLAGS += -DNRF52_PAN_36
CFLAGS += -DNRF52_PAN_53
CFLAGS += -DANT_STACK_SUPPORT_REQD
CFLAGS += -DTRACE_BSC_PAGE_0_ENABLE
CFLAGS += -DTRACE_BSC_GENERAL_ENABLE
CFLAGS += -DNRF_LOG_USES_UART=1
CFLAGS += -DSENSOR_TYPE=0x7B
CFLAGS += -DS212
CFLAGS += -DCONFIG_GPIO_AS_PINRESET
CFLAGS += -DTRACE_BSC_COMB_PAGE_0_ENABLE
CFLAGS += -DENABLE_DEBUG_LOG_SUPPORT
CFLAGS += -DSWI_DISABLE0
CFLAGS += -DTRACE_BSC_PAGE_3_ENABLE
CFLAGS += -DTRACE_BSC_PAGE_2_ENABLE
CFLAGS += -DNRF52_PAN_64
CFLAGS += -DNRF52_PAN_20
CFLAGS += -DNRF52_PAN_62
CFLAGS += -DNRF52_PAN_63
CFLAGS += -mcpu=cortex-m4
CFLAGS += -mthumb -mabi=aapcs --std=gnu99
CFLAGS += -Wall -Werror -O3 -g3
CFLAGS += -mfloat-abi=hard -mfpu=fpv4-sp-d16
# keep every function in separate section. This will allow linker to dump unused functions
CFLAGS += -ffunction-sections -fdata-sections -fno-strict-aliasing
CFLAGS += -fno-builtin --short-enums

# keep every function in separate section. This will allow linker to dump unused functions
LDFLAGS += -Xlinker -Map=$(LISTING_DIRECTORY)/$(OUTPUT_FILENAME).map
LDFLAGS += -mthumb -mabi=aapcs -L $(TEMPLATE_PATH) -T$(LINKER_SCRIPT)
LDFLAGS += -mcpu=cortex-m4
LDFLAGS += -mfloat-abi=hard -mfpu=fpv4-sp-d16
# let linker to dump unused sections
LDFLAGS += -Wl,--gc-sections
# use newlib in nano version
LDFLAGS += --specs=nano.specs -lc -lnosys

# Assembler flags
ASMFLAGS += -x assembler-with-cpp
ASMFLAGS += -DTRACE_BSC_PAGE_4_ENABLE
ASMFLAGS += -DNRF52
ASMFLAGS += -DTRACE_BSC_PAGE_5_ENABLE
ASMFLAGS += -DMODIFICATION_TYPE=1
ASMFLAGS += -DSOFTDEVICE_PRESENT
ASMFLAGS += -DBOARD_PCA10040
ASMFLAGS += -DTRACE_BSC_PAGE_1_ENABLE
ASMFLAGS += -DNRF52_PAN_12
ASMFLAGS += -DNRF52_PAN_15
ASMFLAGS += -DNRF52_PAN_58
ASMFLAGS += -DNRF52_PAN_55
ASMFLAGS += -DNRF52_PAN_54
ASMFLAGS += -DNRF52_PAN_31
ASMFLAGS += -DNRF52_PAN_30
ASMFLAGS += -DNRF52_PAN_51
ASMFLAGS += -DNRF52_PAN_36
ASMFLAGS += -DNRF52_PAN_53
ASMFLAGS += -DANT_STACK_SUPPORT_REQD
ASMFLAGS += -DTRACE_BSC_PAGE_0_ENABLE
ASMFLAGS += -DTRACE_BSC_GENERAL_ENABLE
ASMFLAGS += -DNRF_LOG_USES_UART=1
ASMFLAGS += -DSENSOR_TYPE=0x7B
ASMFLAGS += -DS212
ASMFLAGS += -DCONFIG_GPIO_AS_PINRESET
ASMFLAGS += -DTRACE_BSC_COMB_PAGE_0_ENABLE
ASMFLAGS += -DENABLE_DEBUG_LOG_SUPPORT
ASMFLAGS += -DSWI_DISABLE0
ASMFLAGS += -DTRACE_BSC_PAGE_3_ENABLE
ASMFLAGS += -DTRACE_BSC_PAGE_2_ENABLE
ASMFLAGS += -DNRF52_PAN_64
ASMFLAGS += -DNRF52_PAN_20
ASMFLAGS += -DNRF52_PAN_62
ASMFLAGS += -DNRF52_PAN_63
#default target - first one defined
default: clean nrf52832_xxaa

#building all targets
all: clean
	$(NO_ECHO)$(MAKE) -f $(MAKEFILE_NAME) -C $(MAKEFILE_DIR) -e cleanobj
	$(NO_ECHO)$(MAKE) -f $(MAKEFILE_NAME) -C $(MAKEFILE_DIR) -e nrf52832_xxaa

#target for printing all targets
help:
	@echo following targets are available:
	@echo 	nrf52832_xxaa


C_SOURCE_FILE_NAMES = $(notdir $(C_SOURCE_FILES))
C_PATHS = $(call remduplicates, $(dir $(C_SOURCE_FILES) ) )
C_OBJECTS = $(addprefix $(OBJECT_DIRECTORY)/, $(C_SOURCE_FILE_NAMES:.c=.o) )

ASM_SOURCE_FILE_NAMES = $(notdir $(ASM_SOURCE_FILES))
ASM_PATHS = $(call remduplicates, $(dir $(ASM_SOURCE_FILES) ))
ASM_OBJECTS = $(addprefix $(OBJECT_DIRECTORY)/, $(ASM_SOURCE_FILE_NAMES:.s=.o) )

vpath %.c $(C_PATHS)
vpath %.s $(ASM_PATHS)

OBJECTS = $(C_OBJECTS) $(ASM_OBJECTS)

nrf52832_xxaa: OUTPUT_FILENAME := nrf52832_xxaa
nrf52832_xxaa: LINKER_SCRIPT=ant_bsc_tx_gcc_nrf52.ld
nrf52832_xxaa: $(BUILD_DIRECTORIES) $(OBJECTS)
	@echo Linking target: $(OUTPUT_FILENAME).out
	$(NO_ECHO)$(CC) $(LDFLAGS) $(OBJECTS) $(LIBS) -o $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out
	$(NO_ECHO)$(MAKE) -f $(MAKEFILE_NAME) -C $(MAKEFILE_DIR) -e finalize

## Create build directories
$(BUILD_DIRECTORIES):
	echo $(MAKEFILE_NAME)
	$(MK) $@

# Create objects from C SRC files
$(OBJECT_DIRECTORY)/%.o: %.c
	@echo Compiling file: $(notdir $<)
	$(NO_ECHO)$(CC) $(CFLAGS) $(INC_PATHS) -c -o $@ $<

# Assemble files
$(OBJECT_DIRECTORY)/%.o: %.s
	@echo Compiling file: $(notdir $<)
	$(NO_ECHO)$(CC) $(ASMFLAGS) $(INC_PATHS) -c -o $@ $<


# Link
$(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out: $(BUILD_DIRECTORIES) $(OBJECTS)
	@echo Linking target: $(OUTPUT_FILENAME).out
	$(NO_ECHO)$(CC) $(LDFLAGS) $(OBJECTS) $(LIBS) -o $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out


## Create binary .bin file from the .out file
$(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).bin: $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out
	@echo Preparing: $(OUTPUT_FILENAME).bin
	$(NO_ECHO)$(OBJCOPY) -O binary $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).bin

## Create binary .hex file from the .out file
$(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).hex: $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out
	@echo Preparing: $(OUTPUT_FILENAME).hex
	$(NO_ECHO)$(OBJCOPY) -O ihex $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).hex

finalize: genbin genhex echosize

genbin:
	@echo Preparing: $(OUTPUT_FILENAME).bin
	$(NO_ECHO)$(OBJCOPY) -O binary $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).bin

## Create binary .hex file from the .out file
genhex: 
	@echo Preparing: $(OUTPUT_FILENAME).hex
	$(NO_ECHO)$(OBJCOPY) -O ihex $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).hex

echosize:
	-@echo ''
	$(NO_ECHO)$(SIZE) $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out
	-@echo ''

clean:
	$(RM) $(BUILD_DIRECTORIES)

cleanobj:
	$(RM) $(BUILD_DIRECTORIES)/*.o

flash: $(MAKECMDGOALS)
	@echo Flashing: $(OUTPUT_BINARY_DIRECTORY)/$<.hex
	nrfjprog --program $(OUTPUT_BINARY_DIRECTORY)/$<.hex -f nrf52  --chiperase
	nrfjprog --reset

## Flash softdevice