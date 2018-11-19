licenses(["notice"])

config_setting(
    name = "k8",
    values = {"cpu": "k8"},
)

config_setting(
    name = "aarch64",
    values = {"cpu": "aarch64"},
)

filegroup(
    name = "empty",
    srcs = [],
)

cc_library(
    name = "all",
    srcs = select({
        ":k8": glob([
	    "k8/lib/*.a",
	    "k8/lib/*.so*",
	]),
        ":aarch64": glob([
            "aarch64/lib/*.a",
            "aarch64/lib/*.so*",
        ]),
        "//conditions:default": [":empty"]
    }),
    hdrs = select({
        ":k8": glob([
            "k8/include/*.h",
        ]),
        ":aarch64": glob([
            "aarch64/include/*.h",
        ]),
        "//conditions:default": [":empty"]
    }),
    includes = select({
        ":k8": ["k8/include"],
        ":aarch64": ["aarch64/include"],
        "//conditions:default": [":empty"],
    }),
    visibility = ["//visibility:public"],
)
