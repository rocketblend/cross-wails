# Cross Wails

Docker Image for Cross Compiling [Wails Applications](https://wails.io/)

> [!NOTE]  
> This repository serves as a fork of the original [Cross Wails repository](https://github.com/abjrcode/cross-wails). It was detached from the original due to PRs defaulting to that repository, and adjustments being needed to tailor it for our needs.

## Usage

You can utilize this Docker image as a base image in your own Dockerfile:

```dockerfile
FROM ghcr.io/rocketblend/cross-wails:v2.9.2 as base

# Use `wails build` to build your application
```

For an illustrative example of building Wails applications for Linux AMD64, and Windows AMD64, as well as CI/CD workflows, you can refer to the [RocketBlend Desktop](https://github.com/rocketblend/rocketblend-desktop) project.

> [!NOTE]  
> Does not support ARM architecture due to changes with `libwebkit2gtk-4.0-dev` not allowing multiple architectures to be install at the same time.

## Details

- Image can cross-compile Wails applications that depend on CGO
  - Supports cross compiling to Linux AMD64 and Windows AMD64
    - Can be extended to support more targets and architectures but then I would
      recommend using [goreleaser-cross-toolchain](https://github.com/goreleaser/goreleaser-cross-toolchains/tree/main)
  - You can also use NSIS for creating Windows installers
- It doesn't support cross compiling to MacOS because Wails doesn't support it yet
- The image tag is the same as Wails version, e.g. `v2.9.2`
- The image is adopted from [goreleaser-cross-toolchain](https://github.com/goreleaser/goreleaser-cross-toolchains/tree/main) but with stripped down dependencies
  to minimize the image size and build time
  - It is still a bit over 4GB though :(

For additional insights, you can visit the original author's [blog](https://madin.dev/cross-wails), where they delve into the background story behind this repository.