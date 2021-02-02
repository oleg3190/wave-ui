<template>
  <div>
    <h1>OLEg</h1>
  </div>
</template>

<script>
import { reactive } from "vue";

export default {
  name: "w-oleg"
};
</script>

<style lang="scss">
.w-accordion {
  z-index: 1;

  &--shadow {
    box-shadow: $box-shadow;
  }

  &__item {
    position: relative;
  }

  button.w-accordion__expand-icon {
    color: #999;
  }
  &__expand-icon {
    margin-right: $base-increment;

    .w-accordion--rotate-icon & {
      @include default-transition;
    }
    .w-accordion--rotate-icon .w-accordion__item--expanded & {
      transform: rotate(-180deg);
    }
    .w-accordion--rotate-icon.w-accordion--icon-right
      .w-accordion__item--expanded
      & {
      transform: rotate(180deg);
    }

    .w-icon:before {
      font-size: 1.1em;
    }
  }

  &__item-title {
    position: relative;
    display: flex;
    align-items: center;
    font-size: round(1.2 * $base-font-size);
    padding: 1 * $base-increment;
    user-select: none;
    cursor: pointer;
    border-top: $border;

    .w-accordion__item--disabled & {
      cursor: not-allowed;
      opacity: 0.6;
      -webkit-tap-highlight-color: transparent;
    }
    .w-accordion--no-icon &,
    .w-accordion--icon-right & {
      padding-left: 3 * $base-increment;
    }

    .w-accordion__item:first-child & {
      border-top-color: transparent;
    }

    &:before {
      content: "";
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background-color: currentColor;
      opacity: 0;
      transition: $fast-transition-duration;
    }

    &:focus:before,
    &:hover:before {
      opacity: 0.03;
    }
    &:active:before {
      opacity: 0.05;
    }
    .w-accordion__item--disabled &:before {
      display: none;
    }
  }

  &__item-content {
    padding: (2 * $base-increment) (3 * $base-increment);
  }
}
</style>
